---
title: "Keyboard &amp; Mouse freeze in Ubuntu 10.04!"
date: 2010-05-30
forum: General Help
---

### Post by Rytron on 2010-05-30
Hi.
I installed Ubuntu 10.04 yesterday. Both my keyboard & mouse are a ps2 connection. I have noticed that both have frozen without warning a few times. I then connected a spare USB mouse and that worked. The only fix I have found so far is to reboot. This is very inconvenient!

I can be on for hours and everything is fine. Sometimes soon after logging on, both keyboard & mouse freeze at once.

Note: Even the USB mouse froze once!

My splash screen is also gone! I cannot get in to recovery mode! I think there may be a link between the keyboard and mouse and the video card! I am not certain though.

I've never had an issue with my keyboard & mouse in an previous Ubuntu version dating back to 7.10.

:confused:

Update: I changed the StartUp-Manager Program settings back to their default. I now have a splash screen. However it is split into two separate splash screens and both are completely garbled!

---

### Post by smoka on 2010-05-30
I've seen PS2 devices go bad and cause problems like this, have you tried a different PS2 kbd and mouse? May be a hardware rather than OS issue.

---

### Post by Rytron on 2010-05-30
> **smoka said:**
> I've seen PS2 devices go bad and cause problems like this, have you tried a different PS2 kbd and mouse? May be a hardware rather than OS issue.

Hi smoka. I reckon all ps2 mice would be pretty much the same. However I will try a different ps2 keyboard + mouse. Thanks.

---

### Post by Rytron on 2010-05-31
Update: This link solved my Splash problem: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by fishbulb1022 on 2010-05-31
I don't think its hardware, as my keyboard and mouse freeze on my laptop as well. I had installed the alpha, and assumed it was something to do with that, but have since done a fresh install and the problem persists, even with all updates installed.

---

### Post by Rytron on 2010-05-31
> **fishbulb1022 said:**
> I don't think its hardware, as my keyboard and mouse freeze on my laptop as well. I had installed the alpha, and assumed it was something to do with that, but have since done a fresh install and the problem persists, even with all updates installed.

This is a major problem! Does anyone know how to solve this? :confused:

---

### Post by fishbulb1022 on 2010-05-31
Have you tried doing a remote login, and checking if anything can be done that way? Thats my plan for the next time it happens, but as you said, it can be a few minutes, or a few hours 'til it happens.

---

### Post by fishbulb1022 on 2010-05-31
Seems we aren't the only ones having this issue, there's a huge thread [http://ubuntuforums.org/showthread.php?t=1478787&highlight=mouse+keyboard+freeze]("http://ubuntuforums.org/showthread.php?t=1478787&highlight=mouse+keyboard+freeze")
I just started looking through it...maybe you can find some help there

---

### Post by Rytron on 2010-05-31
> **fishbulb1022 said:**
> Seems we aren't the only ones having this issue, there's a huge thread [http://ubuntuforums.org/showthread.php?t=1478787&highlight=mouse+keyboard+freeze]("http://ubuntuforums.org/showthread.php?t=1478787&highlight=mouse+keyboard+freeze")
I just started looking through it...maybe you can find some help there

Thank you fishbulb1022. I will check it out.

---

### Post by Rytron on 2010-06-02
> **fishbulb1022 said:**
> I don't think its hardware, as my keyboard and mouse freeze on my laptop as well. I had installed the alpha, and assumed it was something to do with that, but have since done a fresh install and the problem persists, even with all updates installed.

Yes I agree. I swapped my mouse and keyboard and the issue persists!

---

### Post by Steve_32 on 2010-06-03
Try to remove "irqbalance" (sudo aptitude purge irqbalance). This solution helped me.

---

### Post by BF79 on 2010-06-03
same issue  keyboard freezes after login  to ubuntu 10.4  mouse still works   but cant figure out what is causing it

---

### Post by Rytron on 2010-06-03
I am using the same PS2 keyboard but have switched to a USB mouse since early yesterday. Still no freezes so the PS2 mouse may be the issue!

---

### Post by BF79 on 2010-06-03
well i tried to switch the mouse between a ps2 adaptor and then to usb  port but didnt change anything  my issue wasnt with the mouse tho  its a MS comfort curve 2000 105 keyboard 
works fine on my other OS   just weird how it works for a while then it seems like it just freezes  cant do anything with the KB  but mouse works fine  no other issues cant even find any error log  and alls i can do is reboot  
whats even crazier is  when i first installed 10.4  when it was released it worked fine for well over a month and then i got a set of updates and thats when the problems started 
so last night  i fresh installed 10.4 again   and it was working fine untill i ran Update manager and installed my updates 
 so what im thinking is tonight im going to  reinstall  and block out sets of updates and see which sets cause the problem to start  
it has to be a bug in an update  
i ran for well over an hour  w/no updates  w/ nop problems  and as soon as i installed all updates threw medibuntu and conacial thats when it started so buy process of eliminattion ill figure it out may take all night but ill figure it out 
its probaly one of the backport updates  seeing as i have everything enabled in Updatemanager

---

### Post by BF79 on 2010-06-03
i think  running" sudo aptitude purge irqbalance" worked  keyboard seems much more responsive   only time will tell  i will response if it don't work  but as of know it seems all fixed  thanks steve32 
it seemed like the usb was being turned off  but i didnt think it to be an irq problem cuz nothing was happening to my mouse   i know this i wouldnt be able to type this far if it didnt work  it would have locked up by the second sentence   thanks again steve32

---

### Post by fly32 on 2010-06-05
I have 2 computers (one I built -- asus mb with nvidia -- and the other a Dell).   The one I built was working fine until I installed Docky, then it started freezing, so I removed it.  However, after removing Docky, my mouse started freezing.  I tried everything posted to no avail, so I had to reinstall and leave it alone.

The Dell computer worked fine on 9.1 for over a year so I upgraded it to 10.04 and the keyboard freezes after a few key strokes.  It's never the same point - sometimes less than 5, other times it'd be over 100 strokes.

Seems to be a pretty nasty bug...

---

### Post by fishbulb1022 on 2010-06-06
I've been looking though several threads on this issue for the past few days and there are two things I would suggest. The first is to use metacity instead of compiz. You'll lose your desktop effects, but you'll gain stability. To switch to metacity, hit alt-f2 and run "metacity --replace" (to switch back to compiz, run "compiz --replace").

The other thing to try would be to upgrade to the mainline kernel. To do that, go here [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and just copy and paste the code into a terminal. Its very simple, seems to have worked for me, and I got to keep compiz enabled.

---

### Post by Rytron on 2010-06-14
For about 2 weeks, I have been using my USB mouse with a PS2 keyboard with no issues. Then I turned on my PC yesterday and the USB mouse froze. So I again got out my PS2 mouse and that now is more stable. Now and then the PS2 mouse also freezes and I must reboot. This wont turn me off Ubuntu but it could make new users leave Ubuntu forever. What is the proper solution to this? :confused: :mad:

---

### Post by Rytron on 2010-06-16
> **Steve_32 said:**
> Try to remove "irqbalance" (sudo aptitude purge irqbalance). This solution helped me.

Hi Steve_32.
Have you noticed your system to be slower now since you got rid of irqbalance or is it just as fast? More info on it here: [http://packages.ubuntu.com/lucid/irqbalance](http://packages.ubuntu.com/lucid/irqbalance)
Do you have 1 CPU or do you have a multiple CPU setup?

---

### Post by Steve_32 on 2010-06-16
@Rytron: I have a single-core Pentium 4 processor with Hyper-Threading technology, and I did not notice any difference in performance. I compared the old version irqbalance (0.55-2.4), because the new versions does not work for me. I guess irqbalance does not affect for single-core processors with Hyper-Threading.

---

### Post by Rytron on 2010-06-17
I removed irqbalance yesterday. I have had no mouse/keyboard freezes since. Knock on wood.

---

### Post by daemonfly on 2010-06-17
Just to add another aspect to this issue, I just tried a freshly downloaded 64-bit 10.04 desktop iso, and installed it within VMWare on my laptop. Keyboard worked throughout the entire process *until* the final restart to the login screen. No keyboard whatsoever. So, I can't even try any of the listed fixes in the other thread, as I can't even type them.

This is after making the mistake of updating my one server to the latest available updates, and having all the keyboard issues there.

:(

---

### Post by Dlambert on 2010-06-18
i removed irqbalance and it still freezes, the mouse and keyboard freeze

---

### Post by Rytron on 2010-06-19
> **Dlambert said:**
> i removed irqbalance and it still freezes, the mouse and keyboard freeze

Try one or both of these in BIOS:
Disable USB Keyboard/Mouse Legacy Support
Turn off HPET in the power section

Also try resetting BIOS to the default settings.

---

### Post by keithwwalker on 2010-06-19
When are they going to solve this problem?
Major f***up, no problems with version 9

My kb and mouse only freezes in my browser, firefox.  I suspect it has something to do with the flash plugin, but I can't prove it.

---

### Post by brad_c6 on 2010-06-19
Thank You!! Fixed my problem immeadiatly!

---

### Post by Rytron on 2010-06-20
> **keithwwalker said:**
> When are they going to solve this problem?
Major f***up, no problems with version 9

My kb and mouse only freezes in my browser, firefox.  I suspect it has something to do with the flash plugin, but I can't prove it.

Remove flash. Then see does the freezing happen in Firefox.

---

### Post by keithwwalker on 2010-06-25
OK I disabled shockwave flash 10.1 r53 in my add in console.  Will see if that works.

> **Rytron said:**
> Remove flash. Then see does the freezing happen in Firefox.

---

### Post by psychomichael on 2010-09-24
Has anyone found a fix for this yet? I've been using mine for over a month now and it has worked great since switching from ps/2 to USB, but after a recent update I'm having the same problem with the mouse & keyboard freezing up. REISUB doesn't work and I have to hard reboot the computer.

---

### Post by psychomichael on 2010-09-24
Okay...testing now, but I think I found the update that caused the problem...for me at least. I hope it helps everyone else too. I followed the instructions at:
[http://hartmansblog.blogspot.com/2010/06/how-to-undo-and-update-in-ubuntu-lucid.html](http://hartmansblog.blogspot.com/2010/06/how-to-undo-and-update-in-ubuntu-lucid.html)

I found some security updates and "fglrx-modaliases". That changed from version 4 to version 5, so I forced the version back and at the moment (knock on wood) it's working. If I don't repost, it worked. ;)

---

### Post by shavo0915 on 2010-10-15
try this i was having a similar issue in both 10.04 and 10.10 and this worked.

[http://ubuntuforums.org/showpost.php?p=9427926&postcount=1](http://ubuntuforums.org/showpost.php?p=9427926&postcount=1)

---

### Post by shavo0915 on 2010-10-15
oh and do a sudo update-grub for the changes to take effect and reboot.

---

### Post by Dlambert on 2010-12-03
Mine was caused by the BCWL 43XX firmware cutter, i removed this, and the installed BCMWL STA driver and it worked fine.

---

### Post by jcannonsr on 2010-12-26
Same issue on a Compac Desktop P4. I did try gnome failsafe at logon, which supposedly disables compiz, so I could do the updates and see if maybe that would fix it. It DID NOT FREEZE in gnome failsafe, but the updates did not fix it. Still looking for the solution.

---

### Post by mandelcat on 2011-02-16
The suggestion to:

Disable USB Keyboard/Mouse Legacy Support in the BIOS worked perfectly for me.

Thanks!

---

### Post by john.quinn on 2011-06-11
> **shavo0915 said:**
> oh and do a sudo update-grub for the changes to take effect and reboot.
Yep, that worked for me. Thanks!

---

### Post by Rebelli0us on 2011-06-11
How do you know that the Keyboard & Mouse freeze ?  Could be the entire OS freezes or hangs, and when that happens the keyboard & mouse also become unresponsive.

---

