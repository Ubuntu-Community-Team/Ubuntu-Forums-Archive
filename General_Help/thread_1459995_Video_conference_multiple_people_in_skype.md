---
title: "Video conference multiple people in skype"
date: 2010-04-22
forum: General Help
---

### Post by duke.tim on 2010-04-22
*Note I have solved this with a script in #4 check it out! *you will need to set audio yourself (the easiest way if you don't know how is turn your speakers up so they can hear through your mic)*

I have been working on a way to have a multiple user video conference in skype. I hope via the various ways stated below to setup a server that I can give a command to call me and various others to allow us to see each others video. here is what I have so far. *note for new users on kde use kdesu not gksu

So the first step is getting skype to run multiple instances 

#1 I can login skype switch users and run both at the same time
	ISSUES: the skype windows are on different desktops and split video and audio between 	different calls.
#2 I run skype under different users on my main login as such

	xhost +local:username
	gksu -u username1 skype / secondary
	gksu -u username2 skype / secondary


#3 I run one skype on linux and another on Vbox
	
	ISSUES: video slow and almost unresponsive on the virtual machine. (device specific) No web 	cam

*If this works normal users could do a group conference for sound and then individual video's (make sure to mute them).
also hope you have good internet connection for this.

---

### Post by duke.tim on 2010-04-23
Bump/Update Okay with #2 I believe video will need a program to capture the feed and split the feed to multiple instances of skype.

---

### Post by duke.tim on 2010-04-24
I found out two things after experimenting #1 don't use aoss
#2 don't use pulse audio either(you can use pulse audio it just really irritates me). after that skype worked fine. all thats left is waiting for some people to test it with and fixing the video!

---

### Post by duke.tim on 2010-06-07
Here is a script I made to simplify the process just replace username 1 & 2 with usernames that you have on your system. Save it as Multiskype.sh in /home/username/bin .

```
#!/bin/bash
# Made by Tim Hanneman :P

echo "Skype Super Session Script"
xhost +local:username1
xhost +local:username2
echo "xhost step complete"
skype &
gksudo -u username1 "skype" &
gksudo -u username2 "skype" &
echo "skype startup"
exit
```

You then need to give it rights
```
chmod 700 /home/username/bin/Multiskype.sh
```
now make sure this line is in your /home/username/.profile
PATH="$HOME/bin:$PATH"

To use simiply type Multiskype.sh 
(if it doesn't work got to /home/username/bin/)and type ./Multiskype.sh

---

### Post by ftmichael on 2010-09-06
I'm running 10.04 (Lucid) and found that Skype (**version 2.1.0.81-1ubuntu5**) will run multiple instances without my needing to do anything - no Multiskype.sh or anything else required.  I created a second user account so I could be logged in on both instances of Skype on the same computer.  Calling the test number simultaneously with both accounts worked perfectly.  My next conference call is next week, so I'll edit this post after that to confirm - or not - that it all worked.

---

