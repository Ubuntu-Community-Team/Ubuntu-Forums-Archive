---
title: "Motion configuration with mutliple webcams and ip cameras"
date: 2011-12-19
forum: General Help
---

### Post by ndmaque on 2011-12-19
Intended for people trying to configure 'Motion' with a mixture of cheap usb web cameras and IP cameras but can't get multiple and mixed cameras configured.

I couldn't find an example of configuration files for this type of set-up anywhere and guess you can't either. I assume you have motion installed and are up and running with one webcam. 
This is just about the motion.conf and threadX.config files only.

I wanted the jpg/avi files in a different folder for each camera, and each camera to be viewed in a browser.

First the location of the .conf files, for Ubuntu the best place to put all 4 .conf files is in
/etc/motion
for other distros they may be better of elsewhere, see the motion site for info.

When in the right location you do not need to specify where they are when you run motion, but you can actually put them anywhere you like and use the -c opt like this 
motion -c /path-to-file/motion.conf 


Most of my trouble was that the config files were not actually being found but motion doesn't tell you (this could have been my fault after misreading the website). 
It was only when i ran motion in daemon mode did it actually tell me the files were missing and being skipped, motion still ran as such but not as i expected.
make sure the files are readable and writeable to you.

**Multiple camera mode**
Confusingly when using multiple cameras the motion.conf kinda changes it's purpose and simply holds all the global or common settings for all cameras and each camera will need it's own threadX.conf with it's individual settings.

With **3** cameras i needed the main motion.conf file and **3** threadX.conf files.
So that's 4 files in total, motion.conf which is now just a global setter plus thread1.conf thread2.conf and thread3.conf.


**motion.conf**
I ended up commented these out when i was testing but not totally sure if it helped.
It's prolly ok to leave motion.conf pretty much as it was but this works fine for me and that's how it's gonna stay now it's fully working.

;netcam_url value
;target_dir value
;webcam_port 8081
;videodevice /dev/video0

The labels and timestamps wern't clear in my jpg's due to £5 webcams unless i set this
text_double on

Now it's all working properly i start motion silently (daemon mode). 
daemon on 

It's a good idea to store the PID on start up, it may be useful later.
process_id_file /home/ndmaque/motion/motion.pid

i have 3 cameras in total (2 usb webcams and a Foscam IP) so needed to enable 3 thread config files at the very bottom of motion.conf. 

 thread /etc/motion/thread1.conf
 thread /etc/motion/thread2.conf
 thread /etc/motion/thread3.conf
;thread /usr/local/etc/thread4.conf


**threadX.conf**
The thread.conf files need very little info, this is all i have in mine for now.

**thread1.conf**
videodevice /dev/video0
text_left USBWebcam-1
target_dir /home/ndmaque/motion/images/webcam1
webcam_port 8081

**thread2.conf**
videodevice /dev/video1
text_left USBWebcam-2
target_dir /home/ndmaque/motion/images/webcam2
webcam_port 8082

**thread3.conf**
netcam_userpass admin:mypassword
text_left Foscam IP
netcam_url [http://192.168.0.60/videostream.cgi](http://192.168.0.60/videostream.cgi)
target_dir /home/ndmaque/motion/images/foscam
webcam_port 8083
*IP Cam's generally need a user/pass to be accessed.

If you have two usb webcams you should see video0 and video1 in your /dev folder and the above *should* work. The file folders will be re-created by motion so you can just delete the whole lot anytime.

**Good to go**
We're ready to rock so from the command line...
motion

The reponse confirms it found and loaded all the conf files... 

[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Processing config file /etc/motion/thread1.conf
[0] Processing config file /etc/motion/thread2.conf
[0] Processing config file /etc/motion/thread3.conf
[0] Motion 3.2.11 Started
[0] Motion going to daemon mode

Yay, i can see files pouring into the three folders.

Time to fire up the browser and have a peep.
[http://localhost:8081/](http://localhost:8081/)
[http://localhost:8082/](http://localhost:8082/)
[http://localhost:8083/](http://localhost:8083/)

OMG i can see again, it's miracle!


Bizarely i do not intend to use the zone/motion detection zones thing because even high quality cams trigger when shadows/daylight/trees/reflections move, and don't forget movement is relative so panning the camera will trigger and cause a dump of unwanted files so i set the threshold in the global motion.conf to make sure they never trigger and jpg/avi files are not created.
threshold 1000000 

However, during testing i set the threshold low so the camera's trigger and create files as soon as motion fires up without me having to dash around the house and dance in front of each one.
threshold 1

Because i start my motion with threshold 1000000 i need a method of creating videos when my burglar actually does turn up.

**Arduino Uno**

I have my Arduinos hooked up with motion, smoke and other sensors which make a much better decision if i am being burgled again.
The Arduino's trigger the BeagleBone to kill the process (the PID is in that file we configured earlier) and restarts motion using a different set of .conf files which are set to threshold 1 so it constantly records files
motion -c /path-to-file-always-record/motion.conf

I use the youtube data api to push the videos into my account using 
on_event_end myscript.sh 
and sends me a text and email with all the sensor values. It also posts the data and ftp's the much clearer jpg's into my Drupal site.
After iv'e been robbed Arduino triggers BeagleBone to restart motion with the threshold 100000 .conf again ready for the next burglar.



A £60 PTZ foscam, 2 x £5 webcams, a £12 Arduino Uno and the almighty £60 BeagleBone.
Thank you to Linux, Motion, Drupal and the Youtube cloud for a high quality cheap, flexible and reliable alarm.
Oh yes, a big thanks to my burglar without whom this post would never have happened.

I really hope this helps someone.
(*|*)

---

### Post by audunpoi on 2012-04-19
Hi, and thanks for a very helpful post! I wonder if you would be willing to share your youtube upload script? I'm working on an art project where I use "motion" for surveillance of bird nesting boxes. Thanks.

---

### Post by arfiansyah on 2012-06-25
i have 4 dlink ip cameras,.can  you tell me how to configure those cameras in motion??
is there any other software which can manage ip camera and show it in web browser except zoneminder??
thanks;)

---

### Post by ndmaque on 2012-07-01
arfiansyah

You give very little info as to what the problem is, what have you got running and what fails?

I cannot tell you howto using wi-fi but i offer advice for a wired connection as a proof of concept and once proven you only have to do the wi-fi bit.
It's best to wire up each camera into your hub/switch/router one at a time and configure it's static ip address, disconnect it and repeat for each camera.
You can configure most IP cameras by visiting them in your browser at some address like [http://192.168.0.100](http://192.168.0.100) or whatever the manual says.
Your manual will tell you the default username and password (often admin and admin)
once logged in set the ip address as static

i run this from a terminal to get my own ip address
ifconfig

my laptop ip was 92.168.0.50 and so i set my 3 ip cameras to...
192.168.0.60
192.168.0.70
192.168.0.80

once the cameras are configured you **should** be able to wire them all in to your hub/switch/router at the same time and ping them and visit them in your browser using it's ip address
[http://192.168.0.60](http://192.168.0.60) etc


i can't afford the luxury of Dlink cameras but all IP cam's are pretty much the same to set up.

have you got this far?


if so you can view the camera output at the port you set in in your threadX.conf

in my example above i mention a config file thread3.conf and set this
webcam_port 8083
netcam_url [http://192.168.0.60/videostream.cgi](http://192.168.0.60/videostream.cgi) <-- you may need to change this for dlink


so in my browser i go to 
[http://localhost:8083](http://localhost:8083) 
and you should see the stream for that camera 

NB* the netsream is quirky and you need to edit 
[http://192.168.0.60/videostream.cgi](http://192.168.0.60/videostream.cgi)
works for foscam cameras only

it is easy to work out the correct url for your camera

you need to log in to you camera as admin and on the view camera page (so you can see the cam live)

somwehere in the html of the page there will be an <img> tag with the url inside it
in my case i found  
<img src="http://192.168.0.60/videostream.cgi" />

TIP:
using firefox with the firebug add on, or chrome will help, right click on the video and view the code.

---

### Post by arfiansyah on 2012-07-02
> 
if so you can view the camera output at the port you set in in your threadX.conf

in my example above i mention a config file thread3.conf and set this
webcam_port 8083
netcam_url [http://192.168.0.60/videostream.cgi](http://192.168.0.60/videostream.cgi) <-- you may need to change this for dlink


Can you show me ur motion.conf with those ip address??

---

### Post by ndmaque on 2012-07-03
> **arfiansyah said:**
> Can you show me ur motion.conf with those ip address??

there is nothing in the main motion.conf when using mutliple cameras except global settings.
each camera has it's own threadX.conf and everything is done in those including the ipaddress and port number etc.

the only thing in motion.conf was to enable the threadX.conf lines at the bottom, in my case i had 3 cameras so enabled (uncommented) 3 of them.

Motion.conf only has global settings when you have more than one camera.
this means that each camera can have it's own settings, ie it's own ipaddress, it's own localhost port number and even the overlay text with the name of each camera.

can you ping the cameras? ie are they on the network?

---

### Post by arfiansyah on 2012-07-05
this is my thread1.conf configuration
```
netcam_url http://192.168.0.99/video.cgi

```

```
netcam_url http://192.168.0.99/video.jpg
 
```
i take the netcam_url from motion webhome, thats the url for dlink ip cameras..
but i still didnt see a picture or a video..

---

### Post by arfiansyah on 2012-07-06
a video from my netcam already showed in 
```

localhost:8081

```

how to access that link from other PC??
i didnt see anything in my windows webbrowser...
i'm using VM Ware...

---

### Post by arfiansyah on 2012-07-09
May i ask you??
Where's the motion file located??
I type my 192.168.0.10 in my browser,
Then, it showed all of the file include *.html that we use when we access 192.168.0.10:8080
Where does that file located??

---

