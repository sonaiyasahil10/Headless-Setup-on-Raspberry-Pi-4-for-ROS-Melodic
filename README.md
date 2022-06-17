# Headless-Raspberry-Pi-4-Setup-for-ROS-Melodic


Needless to say before installing ROS on your Raspberry Pi 4 you will need an Operating System to be installed on which later ROS-Melodic will be installed.

There are many OS available out there but in this section we will be installing *Raspbian Buster (Debian 10)* which is no longer a stable release but right now is the latest OS for ROS-Melodic instalation. Notably for Melodic either Stretch or Buster preferred.

Also we will be trying with a **headless setup** i.e, we will try to install the Raspbian OS without the need of an extra Display, Keyboard or mouse.

Raspbian Buster is the fourth version of the Raspbian operating system and is based on Debian Buster.
Raspbian is a free Debian-based operating system optimized for the Raspberry Pi, and Buster is the development code name for Debian 10. In this guide, we'll download and install Raspbian Stretch for use on the Raspberry Pi.

Before moving on [download](https://drive.google.com/drive/folders/1Cus9rOH_-XbNsec-lqWiV9UxXxrr0uHh?usp=sharing) this OS image file : 

## So the flow of tasks is as given:

1) Get an SD Card (mine is 16GB)

2) Format it using SD card using SDCard Formatter (which you can find it [here](https://www.sdcard.org/downloads/formatter/ ) )

3) Use an ethcer or imager to burn the OS on the formatted SD card ( I will be using Raspberry pi imager which you can find [here](https://www.raspberrypi.org/downloads ) )
   1) Open the Raspberry Pi Imager. 
   
         ![image](https://user-images.githubusercontent.com/84728233/144751687-041d5be8-9bd2-4cb9-ad7b-247cf5ec784a.png)
   2)  Click *Choose OS* and Select *Use custom* to write an unlisted image. Here you select the downloaded Rapbian buster image

          ![image](https://user-images.githubusercontent.com/84728233/144751889-7fe18470-7443-4c88-bcd1-b7dc0a3fb19b.png)
          
   3) Click Choose SD card and Select from the list the SD card you want to write to.

   3)  Press Ctrl + Shift + x to open the advanced menu (CMD + Shift + x for Mac OSX).

        ![image](https://user-images.githubusercontent.com/84728233/144751766-6f67407b-7cd2-453a-a8bd-c4071ab92e89.png)

   4) You can either set your Wfi credentails here itself ***or*** follow Step 6 to configure wifi by externally adding 2 files.
   
   5) Scroll down to Configure wifi, check the box and enter your WiFi credentials.

         ![image](https://user-images.githubusercontent.com/84728233/144751810-4ac2a900-6fb9-4cc1-a06a-1629a5ae540c.png)
         
    6)  Click SAVE and flash your OS to your microSD card for your Raspberry Pi! That’s it!


4) Once the image has been written, Raspbian OS is installed. 

6) Now we need to add some more files in the SD card that will enable SSH and will connect to WiFi on the boot. These two files are "wpa_supplicant.config" and "ssh", I have used notepad++ text editir to create the config file.

Create a file named  "wpa_supplicant.conf" and place the below code with your country code, WiFi name, and password. This will connect your Raspberry Pi to the WiFi network.

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=IN #Your country code

network={
        ssid="My_WiFi" #Your WiFi Name
        psk="123456789"	#Your WiFi password
        key_mgmt=WPA-PSK
}
```
Use any ***Advance IP scanner*** to find 
