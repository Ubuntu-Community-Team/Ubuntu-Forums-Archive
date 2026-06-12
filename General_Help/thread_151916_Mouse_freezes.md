---
title: "Mouse freezes"
date: 2006-03-28
forum: General Help
---

### Post by LanceM on 2006-03-28
Is anyone else having a problem with the mouse randomly freezing? I have not been able to find a pattern yet, but it seems to happen 3-4 times a week and the only way to get the mouse back is to reboot the computer. 

The mouse is the only thing that freezes, the keyboard and desktop still work. is there a way to restart the mouse driver?

---

### Post by zovres on 2006-03-28
Does restarting X (ctrl+alt+backspace) fix the problem?

---

### Post by LanceM on 2006-03-29
I will try that the next time it locks up. Thanks for the suggestion.

Lance

---

### Post by LanceM on 2006-04-26
Restarting X did not fix the problem. It seems the mouse service just turns off. Is there a way to restart the service?

---

### Post by perkele311 on 2006-06-10
I had the same problem with 5.10 and I recently upgraded it to 6.06 and it almost seems like it is happening more often. but restarting x never works I usually gotta restart the whole machine also.. I am looking for the reason this is an issue cause its gotta stop.

---

### Post by LanceM on 2006-06-10
I am happy I have not upgraded yet. I wonder if it has something to do with the hardware itself. I have an Ubuntu box at work that has never had this problem. I only have this problem with my Dell at home.

---

### Post by cwmccabe on 2006-06-10
[QUOTE=LanceM]Is anyone else having a problem with the mouse randomly freezing?[/QUOTE]

Yes, but fairly infrequently.  What is your hardware?  I'm on a Toshiba laptop, Satellite L25-S119.  From these responses, now I'm a little more worried about moving to Dapper (I'm on 5.10 now).

(**Edit**: I'm using a USB wheel mouse by Logitech.)

---

### Post by perkele311 on 2006-06-12
I am on a dell C600 with pretty compatable hw for everything I have put on it from slackware to gentoo...  so this is the first issue with hw I have..

---

### Post by LanceM on 2006-06-12
Mine is a Dell B110. Mine locks up at least once every-other day. Sometimes though, it will lock up 2-3 times in one day. I am using a PS2 mouse right now, I think I am going to try a USB mouse and see if that helps.

---

### Post by perkele311 on 2006-06-12
After you posted I decided to try out a USB intellimouse and since then it has still frozen once already so.. I am gonna try to focus on getting the touchpad reliable.

---

### Post by standards on 2006-06-12
I'm having similar problems. Sometimes the mouse freezes AND disappears, and sometimes it's still visible. Usually I'll be working with gedit but I was just using Azureus (and no gedit) and it did it again. If I unplug/replug the mouse it works fine- haven't tried rebooting X. 

I did not have this problem with any of the Dapper betas (since flight 7). I'm using a USB microsoft optical mouse w/ 6.06 x386.

---

### Post by cwmccabe on 2006-06-17
I gambled and upgraded to Dapper.  And guess what, the mouse is now freezing once or twice a day.  But I realized that when this happens, the touchpad does not freeze.  Unfortunately, I can't remember if I tried the touchpad when I was having the freeze problem on Breezy (I normally hate using the touchpad).  Unplugging the mouse and plugging it in again doesn't help.

**Edit:** I solved my problem by following post #8 here: [http://ubuntuforums.org/showthread.php?t=189572](http://ubuntuforums.org/showthread.php?t=189572)  I had been using the *fglrx* module, carried over from 5.10.  I switched to *ati* and haven't had a freeze-up since (I'll post again if I do).

**Edit #2:** Of course this means that I can no longer use 3DDesk...

---

### Post by perkele311 on 2006-06-23
At the end of the thread you posted the person recommended kubuntu because "it doesn't use fglrx module" has anyone else tried this because the mouse thing is getting on my nerves and if kubuntu doesn't have the problem I want to migrate possibly

---

### Post by perkele311 on 2006-06-24
I switched to kde and I have gone all last night and today without a freeze up. So I think I might be done with this problem..

---

### Post by perkele311 on 2006-06-24
nevermind I am just freezing up every few days once  after the switch to kde.. which is still weird to me but it is alot more tolerable..

---

### Post by ifokkema on 2006-06-24
That's weird... How can a video-drive mess up a mouse? Well, I've got ATi too, and my PC used to freeze up completely, not just the mouse... Had it fixed by disabling lots of drivers under X.

Either way, if it's just the (USB) mouse, you could try this:
```
sudo /etc/init.d/hotplug restart
```
This works for my colleague who has this problem sometimes. Also, unplugging and replugging your mouse (as suggested) helps sometimes.

But I remember, back in the days when I was still an active Windows user, that a PS/2 device can't be plugged in when your PC is running. I was told that you NEED (?) to turn off your PC first. If this still holds, unplugging/replugging a PS/2 mouse would not help then :)

---

### Post by cwmccabe on 2006-06-24
I have no idea why a video driver would be related to this problem.  Anyway, it has now been about a week since I switched from *fglrx* to *ati* and my mouse hasn't frozen a single time.  Also, it was definitely the mouse alone that was freezing on my computer.  As long as I used the touchpad in place of the mouse after it froze, I could keep working and have no other problems (except far less often when all of X would subsequently lock up).

Thanks for the *hotplug restart* tip.  :)

---

### Post by perkele311 on 2006-06-25
yea I will just have to give up on the touch pad and try a USB mouse and try to restart hotplug.. but this is the weirdest problem I have ever had.. hopefully maybe a update or something will come along for a more permanent fix for me personally.. but thanks..

---

### Post by melotron on 2006-07-06
high folks. It seems the problem is related to the speedstep technology the chips on the Dell C600 has or the cpu scaling (which as I understand should be the same thing). I used to work on breezy and had the same problem with the mouse freezing or even dying altogether (Dell C600 PIII 1Ghz with an ATI video card) and fixed it by changing the default module that was loaded when booting. BTW, this happened using the touchpanel, and things got really worse when using a PS/2 mouse (jerky horizontal movements all of its own, dissapearing and appearing at lower left corner, etc.) I must mention that I have used RedHat 7 and the old Mandrake 10 distros and nothing of this ever happened.

The following link should explain fairly well what to do. I'm not sure wether this has another effect on the cpu (e.g. might fry your box :( ). Perhaps you could rumage a little bit more and see what this change might do as well.

[http://www.ubuntuforums.org/showthread.php?t=75598&highlight=cpufreq](http://www.ubuntuforums.org/showthread.php?t=75598&highlight=cpufreq)

However, I also gambled and upgraded to Dapper. After some experimenting and major crashes I finally decided to reinstall Dapper from scratch and the same problem arose once again, mouse freezes for about 1 sec and then moves again, provided I don't stop trying to move it, otherwise sometimes it freezes completely and must reboot (again the touchpad). If i use a PS/2 mouse, hell arises on my screen.

Logically, I applied the same solution that had worked in Dapper and things went smoothly for some time until I did a major automatic update (what was I thinking?). Haven't applied the patch again and have been looking for other solutions. I will try the old patch as soon as i get back home tonight and then post the results. However, here is another link to a possible solution, similar in nature but loads up the ACPI CPU throttle module instead of the Intel ICH module. Haven't tried it out as I just found it googling around.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/16416](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/16416)

Hope any of these ideas help. Please post back to know if they did the trick for you.

---

### Post by melotron on 2006-07-06
OK. I did the cpufreq and it works like a charm. My mouse is not jerking around or freezing anymore. My log used to print something like "synaptics touchpad lost synchro.." and now it does not appear any more.

Hope this helps you.

One last advice, beware when you make an update, as the cpufreq file might get "reupdated" as was my case. I remembered having done this same thing on the new dapper install and then did a mayor update and the problem started all over again.

---

