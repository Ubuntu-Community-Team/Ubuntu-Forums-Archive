---
title: "Cannot login anymore"
date: 2010-11-02
forum: General Help
---

### Post by tembares on 2010-11-02
Hello all,
I cannot log in into Ubuntu anymore.
I had Ubuntu 10.04 installed. My log in setting was 'automatically log in'.
Later I upgraded to 10.10. When I changed the password settings to 'Show the screen for choosing who will log in' I cannot log in anymore.
When I restart the laptop I see a screen with my name. When I click on it I hear a short sound and cannot enter a password.
I made a short video of the log in procedure:[http://www.youtube.com/watch?v=s9rvya78Yr0]("http://www.youtube.com/watch?v=s9rvya78Yr0")

Please, can anyone give me some advice?
When I go to System->Administration->Login Screen I cannot 'Unlock'. So I cannot change the setting back to Automatically login.

The way I log in into GUI is to:
- go into recovery mode
- log in as root
- log in as myself
- start 'startx'

Please, can someone tell me what to do!

Thank you in advance!

---

### Post by Hoopz on 2010-11-02
If you hit Ctrl-Alt-F1 it will take you to a text mode login.  Can you log in that way?  Then you can try some suggestions here [http://ubuntuforums.org/showthread.php?t=1023326](http://ubuntuforums.org/showthread.php?t=1023326)

---

### Post by Hoopz on 2010-11-02
Try this from text mode

1) logged in
2) startx
3) sudo gedit /etc/gdm/custom.conf
4) changed AutomaticLoginEnable to false

Copied this from the link in my previous post

---

### Post by tembares on 2010-11-04
> **Hoopz said:**
> Try this from text mode

1) logged in
2) startx
3) sudo gedit /etc/gdm/custom.conf
4) changed AutomaticLoginEnable to false

Copied this from the link in my previous post

Thank you very much for your answer.
This does not solve my problem, because I have another issue than where you describe the solution for.

When I turn on my laptop and start in 'normal' mode, then I see a screen with 'usernames'. It is me and guest.
When I click on my name I hear a short sound and that is it. I can not enter my password or whatever.
The only thing I can do is Restart, Suspend or Shut down (maybe you know in which screen I am in now).

Please have a look at my YouTube video. There you see exactly what I mean. It says more than words -> [http://www.youtube.com/watch?v=s9rvya78Yr0]("http://www.youtube.com/watch?v=s9rvya78Yr0")

---

### Post by wojox on 2010-11-04
Try to [reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by tembares on 2010-11-04
> **wojox said:**
> Try to [reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

That is what I already did. It did not help.
I think something is really corrupt :-(

---

### Post by Hoopz on 2010-11-04
You had automatic login enabled before you upgraded so i figured it was worth a shot to try and disable that and see what happens.

---

### Post by tembares on 2010-11-06
> **Hoopz said:**
> You had automatic login enabled before you upgraded so i figured it was worth a shot to try and disable that and see what happens.

I enabled automatically login again.
This worked and I do not have to start in recovery and so on.
But... still I have the issue that I cannot protect my laptop with a password.
If someone can help me with that, I would be very glad with that.

---

