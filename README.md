# HSP

## Home Security Project
This project is made for monitoring the door if it is opened before entering the correct password.

The unauthorized entering will send a request to [RaspberryPi](https://www.raspberrypi.org/) server, which takes pictures of the opened door using [PiCamera](https://picamera.readthedocs.io/en/release-1.13/#) as it send trigger to the event service provided by [IFTTT](https://ifttt.com/maker_webhooks) that send a Line message to my mobile phone in my case.


## Features
### Keys
* '#': Enter
* '*': Delete

### Modes
#### AlertMode
Press Enter without typing anything will enter the AlertMode.

In AlertMode, the Hall Effect Sensor will be monitored. Once the value is out of threshold range, an alert will be triggered and a noisy sound will be played.

To leave AlertMode, simply type the password without pressing enter needed.


#### HallMonitorMode
Enter "0" to go to this mode.

Monitor current reading of the Hall Effect Sensor and show the current threshold.


#### HallThreshModifyMode
Enter "1" to go to this mode.

Modify thresholds through keypad.

At the end of HallThreshModifyMode, HallMonitorMode is called.


#### Toggle Buzzer
Enter "8" to toggle buzzer enabling.


## Note
Two extra files "HSP/HSP_CallsAndPswd.h" and "server/Keys.py" have to be added since it was ignored.

It should be something looks like the following, 


#### HSP/HSP_CallsAndPswd.h
``` C++

// HSP/HSP_CallsAndPswd.h

// The Arduino script will read this file to set wifi, passwords and send proper request to the server.
// Alternatively, the TRIGGER can be IFTTT requests if there is no server envolved.

#ifndef CALLS_AND_PSWD_H
#define CALLS_AND_PSWD_H

#define WIFI_SSID "[wifi_ssid]"
#define WIFI_PSWD "[wifi_password]"
#define ENTER_PSWD "[password]" // for opening the door without sending an alert

#endif

```

#### server/Keys.py

``` python

# server/Keys.py

# These will be passed to IFTTT 
#   as "GET https://maker.ifttt.com/trigger/[start_event_name]/with/key/[key]"
#   with a json file that contains {value1, value2}.
EventName ='[IFTTT Event Name]'
Key = '[IFTTT Key]'

# A folder named below must be exists on your Google Drive
Project_Root_Name = 'HSProject'

```

## Hardware 
TODO

## Extra Libraries
#### Arduino
* [Keypad Library for Arduino](https://playground.arduino.cc/Code/Keypad/)
#### Python-3.5
* [Flask-1.0.2](http://flask.pocoo.org/)
* [PiCamera-1.13](https://picamera.readthedocs.io/en/release-1.13/#)
* Google APIs
* [PyDrive-1.3.1](https://pythonhosted.org/PyDrive/)
## TODO
* ~~Upload Pictures to Google Drive~~ (done @190602)
* ~~Add an alert dismiss message.~~ (done @ 190502)
* ~~Camera Event for RPi.~~ (done @ 190502)
* ~~Can Do More Buzzer Inticator Music~~ (del @ 190422)
* ~~Check function for Hall Effect Sensor Readings.~~ (done @ 190413)
* ~~Modify through a RA. (requires hardware modifications.)~~ (del @ 190412)
* ~~Buzzer Part~~ (done @ 190322)

