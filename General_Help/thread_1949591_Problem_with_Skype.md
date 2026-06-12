---
title: "Problem with Skype"
date: 2012-03-30
forum: General Help
---

### Post by beceraful on 2012-03-30
I can not up to Skype , i want to talk with somebody on skype i click on the green headset but nothing , not lifted :X:X. Please i want to talk in skype with friends , but i don't know what to do.

---

### Post by bobman321123 on 2012-03-30
What version of Ubuntu are you running?

---

### Post by beceraful on 2012-03-30
2.2 . I am with ubuntu 11.04 , and i think that skype 2.2 is the typical skype version on 11.04

---

### Post by bobman321123 on 2012-03-30
What exactly happens? 
Does skype make the call? 
No audio?
No video?
Freezes when you try to call?

---

### Post by bobman321123 on 2012-03-30
(Many other users seem to be having this problem. There hasn't been a fix as far as I have found.
You *might* want to try upgrading to Ubuntu 11.10, as that is the most current stable release at this point. 
Let me know if that helps.)

---

### Post by beceraful on 2012-03-30
No sound , no video , when i call someone writes - problem with conducting sound . The 3 options that have them, one for the handset (ring), it has a further 2 not working.
At least count on me to hear such talk, even if I can not hear what they say

I can't put ubuntu 11.10 only 11.04, is there any other way?

---

### Post by bobman321123 on 2012-03-30
You say they can hear you?
If they can hear you, it might be a problem with your sound driver.
The default ubuntu sound driver is pulseaudio. 

Try this. 
Turn skype off.
Go in terminal.
```
pulseaudio --kill
```
Then try your skype call. 
When you're done, go back and type ```
pulseaudio --start
```

Let me know if that works.

---

### Post by BertN45 on 2012-03-30
You do not give very much information, so trying to guess:

If you use an USB device/headset for Skype and the speakers on another audio output, you have a small problem with Ubuntu. Their sound configuration applet is incomplete.

You need "pulseaudio volume control" from the Ubuntu Software Center. _During_ the Skype test call go to the playing and recording tab and select the USB device for that application. Pulse-audio will remember it forever and use the USB device from now on for Skype. 

In the newest version of Skype, this is also the advice in the audio configuration tab of Skype.

---

### Post by beceraful on 2012-03-30
I am not having install pulseaudio , i was having it , but now it's deleted , if i installed pulseaudio everything will be fine ?

what i have to write in the terminal to install ubuntu sudo then ?

I installed pulseaudio , now i will see what can i do , i will make this example's that bobman says.
My english is not very good but it's not bad too.

______________________

Now , when i write this ---> it writes me this --> Failed to kill daemon: No such process
When i write pulseaudio --start it's not giving me information for somethink

---

### Post by bobman321123 on 2012-03-30
To get into the terminal, press the windows key, and type "terminal" in the bar that shows up.

You get to the software centre by using the same bar, but typing "software center"

Follow Bert's instructions and install "pulseaudio volume control" from the software center.

---

### Post by beceraful on 2012-03-30
bobman , now i called one person in to skype and obtain, he managed to raise with me a word normally , maybe the problem is solved , when i see that he can agreed and call , i will see more about that and if i have problem with skype again i will write in this thread. 
Thanks :)

The skype problem is solved , thanks again , can i made somehow that i want to talk with the person/s and to heard them what they say , ( sound ) , when i installed pulseaudio , can i do somethink to fix and the previous problem ( where i have no sound please )

---

### Post by bobman321123 on 2012-03-30
I didn't entirely understand that, but you're saying it's fixed?
No problems now?

---

### Post by beceraful on 2012-03-30
On the skype yes , no problems. Skype problem is solved . But the last problem is the sound , please tell me what to do , terminal information of something or ?

I am writing in terminal , i write gnome-alsamixer and open something , white page and nothing else

Please tell me what to do

---

### Post by bobman321123 on 2012-03-30
Could you please tell me exactly what's wrong with your sound?

---

### Post by beceraful on 2012-03-30
Now , 5-6 months i do not have sound , since nothing was wrong , 3 4 months later , since I'm on Linux , i have no sound and i don't know why. I fixed the skype problem, and i think also that and the sound problem has a solution. 

Now i fixed the skype problem , i found that i do not have an alsamixer , i install gnome-alsamixer , when i write gnome-alsamixer it writes me this


(gnome-alsamixer:6890): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

I don't know what to do , i think if i could get in gnome-alsamixer options i could fix the problem or i don't know , please tell me variants

---

### Post by bobman321123 on 2012-03-30
Does your whole computer not have sound? Or does just skype not have sound?

---

### Post by beceraful on 2012-03-30
I have sound on my whole computer , now i am not having sound anything and i am 100 % sure , that's because maybe alsamixer's options are not adjusted. If and that's not working maybe is something else , but at the moment i think the whole problem is gnome-alsamixer , look up at the previous reply about the failed connection please.

If you know how much I miss listening music

---

### Post by bobman321123 on 2012-03-30
Did you run the ```
pulseaudio --kill
``` I gave you earlier?
If so, you'll need to run ```
pulseaudio --start
```.
Let me know if that works.

---

### Post by beceraful on 2012-03-30
> **bobman321123 said:**
> Did you run the ```
pulseaudio --kill
``` I gave you earlier?
If so, you'll need to run ```
pulseaudio --start
```.
Let me know if that works.

when i write pulseaudio --kill it writes me ----> E: main.c: Failed to kill daemon: No such process 

when i write pulseaudio --start it writes me nothing.

---

### Post by bobman321123 on 2012-03-30
if it doesn't give you a message, it should be working again. Try playing some music.

---

### Post by beceraful on 2012-03-30
> **bobman321123 said:**
> if it doesn't give you a message, it should be working again. Try playing some music.

I've tryed it but no sound anywhere. Pulseaudio is for skype maybe , skype is fixed but no sound , only they can heard me, the options of gnome-alsamixer , i don't know how to get in there , please look up the 1-st coment again , page 2 or second commentar.

---

### Post by bobman321123 on 2012-03-30
Pulseaudio should be for your whole computer......
Try rebooting. That usually fixes things like that.

---

### Post by beceraful on 2012-03-31
> **bobman321123 said:**
> Pulseaudio should be for your whole computer......
Try rebooting. That usually fixes things like that.

I don't know how
Can you give me the steps to do that , in the terminal , first what , second what please.

---

### Post by beceraful on 2012-03-31
If you want of course

---

### Post by beceraful on 2012-03-31
Now i've looked Volume Control (where is the pulseaudio) 
The first thing is Playback
System sounds : Mono 100 % 

Recording : there's nothing there 

Output devices : Front left - 100 % , frong right 100 % 
Input devices : there's nothing there
Configuration : There's nothing here

It seems maybe pulseaudio is ok and its perfectly working maybe?

But the problem maybe is gnome-alsamixer , when i want to open it , it openeds me a white page with File , Edit , Help , but nothing. How can i open it maybe the whole problem is there ? If you want of course we could see something on pulseaudio too , if you want of course , but i think gnome-alsamixer is the problem.

---

### Post by beceraful on 2012-03-31
Thanks again for the help , when you get on look what i write after your commentar , please

---

### Post by bobman321123 on 2012-03-31
Before we start messing around with your system settings, try restarting your computer. 
This is done 1 of 2 ways.
1.
click the menu in the top right of your screen
select "shut down" from the list
if there's a restart option, click it.
if not, don't worry about it.

2. go in terminal and type ```
sudo reboot
```

If that doesn't help, I'll try investigating gnome-alsamixer.

---

### Post by beceraful on 2012-03-31
I write sudo reboot in the terminal and now? 

Is there chance to fix the sound problem?

---

### Post by bobman321123 on 2012-03-31
Your sound didn't work when your computer started back up again?

try ```
pulseaudio -D
```
if that doesn't work, try this
```
sudo apt-get purge pulseaudio
sudo apt-get install pulseaudio
sudo reboot
```

---

### Post by beceraful on 2012-03-31
I installed them perfectly , cod 1 don't work but cod 2 works , i installed everything and write sudo reboot , but no sound again , another variant?

---

### Post by bobman321123 on 2012-03-31
I'm sorry to say that I'm actually very unqualified to help with sound issues.

My suggestion is to make another thread called "sound playback problems" and hope to find someone who specializes in sound problems. 

I'm sorry I couldn't help more. 

-bobman

---

### Post by beceraful on 2012-03-31
no problem :) Thank you very much :)

---

### Post by cryptotheslow on 2012-03-31
If gnome-alsamixer is not working correctly for you, try using alsamixer instead.

From the Terminal:
```
alsamixer
```

---

