---
title: "&quot;another&quot; audio issue"
date: 2006-05-21
forum: General Help
---

### Post by steinix on 2006-05-21
i almost forgot to say exactly what laptop it is, ibm thinkpad 600e
hello, i have seen the other posting on this similar topic but i didnt have much luck using the tips on my system, so ill post this one, i have an ibm think pad, pentium 2, and i know the sound works as i had win xp on here and it worked fine

	I typed lspci into a terminal window and got the following output, 0000:00:06.0 multimedia audio controller: cirruslogic cs [crystalclear soundfusion audioaccelerator] (rev 01)
	Then i typed esd and got the following, 
alsa lib confmisc.c:560:(snd_determine_driver)couldnot open control for card0
alsa lib conf.c:3479:(_snd_config_evaluate)function snd_func_card_driver returned error: no such file or directory
alsa lib confmisc.c :392:(_snd_func_concat)error evaluating strings
alsa lib conf.c:3479:(_snd_config_evaluate)function snd_func_concat returned error: no such file or directory
alsa lib confmisc.c:955:(snd_func_refer)error evaluating name
alsa lib conf.c:3479:(_snd_config_evaluate)function snd_func_refer returned error: no such file or directory
alsa lib conf.c3948:(snd_config_expand)evaluate error: no such file or directory
alsa lib pcm.c:2090:(snd_pcm_open_noupdate)unkonwn pcm default
	
	That is all the stuff from the terminal, and this is what i did under different menus on the desktop.
1)under system, preferences, multimedia systems selector, i get this error message &#8220;registry is not present or it is corrupted, please update it by running gst-register&#8221; well i typed that in at a terminal and nothing happened.
2)then i tried, system, administration, device manager I see it there, under advanced it displays a lot of stuff, and id display it but i don't know the windows equivalent to ctrl+a (select all)
3)then applications, sound & video, volume monitor, i get  an &#8220;error (vumeter)&#8221; cannot connect to sound daemon please run 'esd' as a command prompt &#8220; which I already listed.
4)then i tried man esd, and tried a couple commands but no go

i am very new to linux, but i want to beleive, if you have any sugestions for me or links that may help id be very grateful, thanks in advance

---

### Post by pedalwrench on 2006-06-11
[http://www.ubuntuforums.org/showthread.php?t=94414&highlight=ibm+600E](http://www.ubuntuforums.org/showthread.php?t=94414&highlight=ibm+600E)

this may help you.  I will be trying it on my TP600E later

:p

---

