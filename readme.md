static void detection_delay_timeout_handler(void * p_context)
{
    uint8_t i,j;
	uint8_t cube_pin_state[12];
	char cube_state[6];

    // Pushed button(s) detected, execute button handler(s).
	// For every 50us or less time, check the state and obtain the current state of adc
    for (i = 0; i < m_button_count;)
    {
        app_button_cfg_t const * p_btn = &mp_buttons[i];
        
		if(p_btn->active_state)
		
			cube_pin_state[i] = 1;
		else 
			cube_pin_state[i] = 0;
		
		app_button_cfg_t const * p_btn = &mp_buttons[i+1];
		
		if(p_btn->active_state)
		
			cube_pin_state[i+1] = 1;
		else 
			cube_pin_state[i+1] = 0;
		
	j = i/2; 
	
	if (cube_pin_state[i] == 1 && cube_pin_state[i+1] == 1) cube_state[j] = 'A'
	if (cube_pin_state[i] == 0 && cube_pin_state[i+1] == 1) cube_state[j] = 'B'
    if (cube_pin_state[i] == 1 && cube_pin_state[i+1] == 0) cube_state[j] = 'C'
    if (cube_pin_state[i] == 0 && cube_pin_state[i+1] == 0) cube_state[j] = 'D'
	
	i += 2;
	
	}
    
