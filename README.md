## Welcome to imp-simple-Motor ##


This is an [electric imp](http://electricimp.com) project for basic positional DC motor control. A simple proportional feedback control loop is utilized.
# Overview #

Slightly more advanced code than the *imp-simple-PWM* project. Two potentiometers are used:  one on the motor shaft and one for you to set the motor position with.


### Device-side Functionality  ###
- pot read 100x/second
- PWM duty cycle updated accordingly from 0-100%
- 20x/second, the controller streams "dashboard" data out serial port for monitoring
- *imp's* **Sampler()** mode used for all ADC potentiometer captures (1000 hz).
- 10x ADC oversampling with averaging for basic noise suppression
- two serial monitoring modes: terminal emulator target, or DAQ software
- each function runs in seperate timer loop
#### Other Features ####

Potentiometer positioning knob centered moves motor to center position. Pot knob moved 25% off center; motor rotates in that direction until its pot is 25% off center too, etc...(IE. 1:1)

 * Controller's current state is held in a table refreshed in realtime.
 * This table (motor[][]) contains: setpoint, motor position, error, duty cycle, etc.
 * If Verbose logging is disabled this machine state can be graphed in real-time via an app such as [DAQfactory Express](http://daqexpress.com) * 
   * Streamed output is comma-delimited list:
     *   [setpoint, position, error, dutyCycle, setpoint_min, setpoint_max, position_min, position_max, direction]
 * H-Bridge is expected to be driven in direction + PWM mode (i.e. two seperate pins)

### Agent-side Functionality  ###
None.
