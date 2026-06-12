---
title: "Systems restarts for no apparent reason"
date: 2011-12-13
forum: General Help
---

### Post by tech291083 on 2011-12-13
Hi,

I have this problem with my Ubuntu 10.04 pc. It keeps restarting for some weird reason. I have no idea as to why this is happening. There is only one OS on the hard drive and that is this Ubuntu. Here is what I am getting as output to the last command in a terminal.

```

james@james-desktop:~$ last
james   pts/0        :0.0             Tue Dec 13 11:52   still logged in   
james   tty7         :0               Tue Dec 13 11:50   still logged in   
reboot   system boot  2.6.32-33-generi Tue Dec 13 11:56 - 11:52  (00:-4)    
james   pts/2        :0.0             Tue Dec 13 11:47 - crash  (00:08)    
james   pts/2        :0.0             Tue Dec 13 11:40 - 11:41  (00:00)    
james   pts/2        :0.0             Tue Dec 13 11:36 - 11:38  (00:01)    
james   pts/2        :0.0             Tue Dec 13 11:29 - 11:33  (00:04)    
james   pts/2        :0.0             Tue Dec 13 11:22 - 11:26  (00:03)    
james   pts/2        :0.0             Tue Dec 13 11:20 - 11:20  (00:00)    
james   pts/0        :0.0             Tue Dec 13 10:47 - crash  (01:09)    
james   tty7         :0               Tue Dec 13 10:46 - crash  (01:09)    
reboot   system boot  2.6.32-33-generi Tue Dec 13 10:46 - 11:52  (01:05)    
james   tty7         :0               Tue Dec 13 10:45 - crash  (00:00)    
reboot   system boot  2.6.32-33-generi Tue Dec 13 10:45 - 11:52  (01:06)    
james   pts/0        :0.0             Mon Dec 12 14:35 - 14:37  (00:02)    
james   tty7         :0               Mon Dec 12 14:35 - 14:37  (00:02)    
reboot   system boot  2.6.32-33-generi Mon Dec 12 14:34 - 14:37  (00:03)    
james   pts/0        :0.0             Mon Dec 12 14:33 - 14:34  (00:00)    
james   pts/0        :0.0             Mon Dec 12 14:32 - 14:33  (00:00)    
james   pts/0        :0.0             Mon Dec 12 12:59 - 14:27  (01:28)    
james   pts/0        :0.0             Mon Dec 12 11:33 - 12:59  (01:25)    
james   tty7         :0               Mon Dec 12 11:32 - 14:34  (03:01)    
reboot   system boot  2.6.32-33-generi Mon Dec 12 11:32 - 14:34  (03:01)    
james   pts/0        :0.0             Sun Dec 11 16:15 - crash  (19:16)    
james   tty7         :0               Sun Dec 11 16:15 - crash  (19:17)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 16:15 - 14:34  (22:18)    
james   pts/0        :0.0             Sun Dec 11 16:11 - 16:11  (00:00)    
james   tty7         :0               Sun Dec 11 16:10 - down   (00:01)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 16:10 - 16:12  (00:01)    
james   pts/0        :0.0             Sun Dec 11 16:09 - crash  (00:01)    
james   tty7         :0               Sun Dec 11 16:09 - crash  (00:01)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 16:09 - 16:12  (00:03)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 16:08 - 16:12  (00:03)    
james   pts/0        :0.0             Sun Dec 11 15:14 - crash  (00:53)    
james   tty7         :0               Sun Dec 11 15:14 - crash  (00:54)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 15:14 - 16:12  (00:58)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 09:02 - 09:02  (00:00)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 09:01 - 09:02  (00:00)    
james   pts/1        :0.0             Sun Dec 11 08:48 - crash  (00:13)    
james   pts/0        :0.0             Sun Dec 11 08:45 - crash  (00:16)    
james   tty7         :0               Sun Dec 11 08:45 - crash  (00:16)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 08:45 - 09:02  (00:17)    
james   pts/0        :0.0             Sun Dec 11 08:07 - crash  (00:37)    
james   tty7         :0               Sun Dec 11 08:07 - crash  (00:37)    
reboot   system boot  2.6.32-33-generi Sun Dec 11 08:06 - 09:02  (00:55)    
reboot   system boot  2.6.32-33-generi Sat Dec 10 11:16 - 14:55  (03:38)    
james   tty7         :0               Sat Dec 10 10:54 - crash  (00:21)    
reboot   system boot  2.6.32-33-generi Sat Dec 10 10:31 - 14:55  (04:23)    
james   pts/0        :0.0             Fri Dec  9 17:54 - 17:54  (00:00)    
james   pts/0        :0.0             Fri Dec  9 17:50 - 17:51  (00:00)    
james   tty7         :0               Fri Dec  9 17:50 - 17:55  (00:05)    
reboot   system boot  2.6.32-33-generi Fri Dec  9 17:48 - 17:55  (00:07)    

wtmp begins Fri Dec  9 17:48:01 2011

```

Please help me. I have a new cpu and power suppy installed just a month ago. Overall the pc was running well before this restart problem started. Thanks.

---

### Post by Roving Sign on 2011-12-13
It may be a hardware problem. I just had similar issue, and it turned out to be that some of the brass motherboard mount posts were not screwed in all the way(and the screws weren't so tight either).

---

### Post by tech291083 on 2011-12-13
> **Roving Sign said:**
> 
it turned out to be that some of the brass motherboard mount posts were not screwed in all the way(and the screws weren't so tight either).


Thanks for the reply. I am not that technically good, but can you please tell me as to what you mean by motherboard mount posts? Thanks a lot.

What does the word crash suggest in the code in my original post (a command called last's output in a terminal)? Thank you.

---

### Post by MartijnNL on 2011-12-13
> **tech291083 said:**
> Thanks for the reply. I am not that technically good, but can you please tell me as to what you mean by motherboard mount posts? Thanks a lot.

The motherboard mount posts are the metal parts which are screwed onto the back panel of your computer. Then the motherboard is screwed on top of these posts. They keep the motherboard away from the panel to prevent electrical shortcuts.

I'm not sure that's the cause of your problem though. It looks a bit like this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706924](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706924)

But it might be worth the effort it to check whether all the hardware is properly connected (including these mount posts). Just be careful not to damage your motherboard or memory. Especially be consious of the risk of an electro static discharge. (Either touch something grounded before handling the motherboard, or use an Electro Static Discharge wristband and attach that to something grounded.)

---

### Post by NautiusMaximus on 2011-12-13
Have you checked the CPU temperature? Overheating can sometimes cause unwanted restarts.

---

### Post by tech291083 on 2011-12-13
Hi,

This is what I got on my screen after the pc restarted itself just a few moments ago.

> Warning ! over clock fail.
Press DEL to run setup.
Press F2 to load default values and continue.
Can you please suggest something as I have pressed F2 and loaded the defaults values a few times earlier but the pc continues to restart itself for no reason at all. Thanks.

---

### Post by MartijnNL on 2011-12-13
That warning seems to indicate a BIOS problem. F2 resets them to default, but perhaps the default don't work correcty for you. It might also be that your CMOS battery is dead. Is your computer showing you the correct time in the panel after you login?

---

### Post by tech291083 on 2011-12-13
My battery is new, bought only 20 days ago. I was also thinking that the battery was dead, but that does not seem to be the case, thanks. I have pressed F2 many times before but after reboot the time in BIOS or date go back to some past date.

---

### Post by MartijnNL on 2011-12-13
> **tech291083 said:**
> My battery is new, bought only 20 days ago. I was also thinking that the battery was dead, but that does not seem to be the case, thanks. I have pressed F2 many times before but after reboot the time in BIOS or date go back to some past date.

Are the correct time and date also gone if you set them now, shut down the system yourself, unplug the computer for a few minutes and then start up again, without having to press F2?

Because if that is the case I think either the battery is dead (despite it being relatively new), or the battery is inserted wrong, or there is something wrong with the BIOS chip or motherboard itself. Did you do ground yourself before installing the new battery? (Thus reducing the risk of any static discharge damaging your hardware.)

---

### Post by tech291083 on 2011-12-13
> **MartijnNL said:**
> Are the correct time and date also gone if you set them now, shut down the system yourself, unplug the computer for a few minutes and then start up again, without having to press F2?

Because if that is the case I think either the battery is dead (despite it being relatively new), or the battery is inserted wrong, or there is something wrong with the BIOS chip or motherboard itself. Did you do ground yourself before installing the new battery? (Thus reducing the risk of any static discharge damaging your hardware.)


The correct time and date seem to disappear no matter whatever way I change things in BIOS. The battery is inserted the right way as checked by a friend of mine as well. (Sorry, I do not doubt your skills) I did not do ground when installing the new battery and I really do not know what you mean by that, thanks. i really some help here as this problems has been giving me nightmates. The pc restarts anytime. Sometimes after 30 mins, 60 mins or just 1 min. I have a new CPU (10 days old), new SMPS (10 days new). My motherboard is

Biostar G31-M7 TE

[http://206.108.48.60/app/en/mb/introduction.php?S_ID=363&tab=3](http://206.108.48.60/app/en/mb/introduction.php?S_ID=363&tab=3)

---

### Post by tech291083 on 2011-12-13
> **NautiusMaximus said:**
> Have you checked the CPU temperature? Overheating can sometimes cause unwanted restarts.
Hi,

Can you please suggest me a program that I can install in Ubuntu 10.04 to monitor the CPU temperature? Thanks. In BIOS it varies after every reboot and generally it is between 40-50 degree C.

---

### Post by tech291083 on 2011-12-13
Hi,

I just installed these software using apt-get command.

 **xsensors**, [B]ksensors, lm-sensors.

[/B][https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by tech291083 on 2011-12-13
Please have a look at the screenshot. Thanks.

---

### Post by asvestomix on 2011-12-13
> **tech291083 said:**
> Please have a look at the screenshot. Thanks.

50 C looks good.
If it is a hardware problem it is a bit difficult for someone to say what it is without the machine on his hands, what you should do is to check the hardware components such as CPU or memories to another motherboard, and see where is the problem. Also try to find from the web the correct voltages  clocks and memories timing settings and try to set them in the bios if they are able to keep the changes.

---

### Post by asvestomix on 2011-12-13
Does this happens if you boot from a live cd or something that does not involve Hdd? To ensure that is not software problem

---

### Post by MartijnNL on 2011-12-13
That is not an abnormal temperature, so I don't think that's got anything to do with it. When I search for your error message and the motherboard type I find a lot of similar messages. It may be that you have to set certain BIOS settings (RAM's timings,voltages and speeds) manually. I searched for:
> Biostar "G31-M7" "! overclock fail"

Also I understand that you put a new CPU in an older motherboard. You might have to update the BIOS software as well. I assume the motherboard supports your CPU?

Regarding grounding, have a look at this page it might explain things better than I do: [https://en.wikipedia.org/wiki/Antistatic_wrist_strap](https://en.wikipedia.org/wiki/Antistatic_wrist_strap)

It is really important to pay attention to this when dealing with memory, motherboards and such. It's easy to damage the memory otherwise. It could be enough to touch the grounding pin of an extension cord directly before handling the hardware. But using a wrist strap (connected to a grounded object) is better. You can easily build up a static charge on yourself just by walking around a bit, especially if the air is very dry.

---

### Post by Roving Sign on 2011-12-13
> **tech291083 said:**
> Hi,

This is what I got on my screen after the pc restarted itself just a few moments ago.

Can you please suggest something as I have pressed F2 and loaded the defaults values a few times earlier but the pc continues to restart itself for no reason at all. Thanks.

Based on that, my next move might be to hit "Del" - and go into the BIOS before the OS boots - and check the CPU speed - make sure any overclock options are turned off - and perhaps even set the CPU to a lower speed - just to see if there is any difference.

It does seem like the BOIS is resetting itself - so perhaps some of the default values arent suitable for your new CPU.

---

### Post by tech291083 on 2011-12-14
> **Roving Sign said:**
> Check the CPU speed - make sure any overclock options are turned off - and perhaps even set the CPU to a lower speed.

It does seem like the BOIS is resetting itself - so perhaps some of the default values arent suitable for your new CPU.


Yes, I have already check the BIOS and the overclocking option is disabled. I never overclock the CPU and I do not exactly know how to do so. Thanks.

---

### Post by tech291083 on 2011-12-14
> **asvestomix said:**
> 
If it is a hardware problem it is a bit difficult for someone to say what it is without the machine on his hands, what you should do is to check the hardware components such as CPU or memories to another motherboard, and see where is the problem.

Yes, I agree with you 100%.

>  Also try to find from the web the correct voltages  clocks and memories timing settings and try to set them in the bios if they are able to keep the changes.I will try to do so, but I am too scared to change these parameters as I am of the opinion that they are adjusted by the BIOS automatically in most of the cases, although I may be totally wrong here. I have hardly seen anyone doing it. Thanks indeed.

---

### Post by tech291083 on 2011-12-14
> **asvestomix said:**
> Does this happens if you boot from a live cd or something that does not involve Hdd? To ensure that is not software problem


Yes, I was trying to install Ubuntu 10.04 and it was constantly restarting itself every 20 mins or so, but I tried atleast 15 times over 6-7 hours and succeeded. It was very frustrating to see the install process being interrupted for no reason, very annoying indeed. My patience has finally paid off. Thanks for your suggestion.

---

### Post by tech291083 on 2011-12-14
> **MartijnNL said:**
> That is not an abnormal temperature.

Yes, I also think so.

> 
When I search for your error message and the motherboard type I find a lot of similar messages.


Thanks for spending time for my issue. I also tried to do so, but not that precisely. I will do this again.

> 
It may be that you have to set certain BIOS settings (RAM's timings,voltages and speeds) manually


You are right, but I am not sure how to set all those settings manually and which official BIOS/Motherboard guide to refer to while doing so. But I will look at the motherboard manual see what I can do. Please keep suggesting me anything with regard to my motherboard model. 

> 
Also I understand that you put a new CPU in an older motherboard.

Yes, it is Pentium Dual Core E5700 3.0 GHz

> I assume the motherboard supports your CPU?

Yes, it does.

> You might have to update the BIOS software as well. 

If so, then I do not know how to do so? If I am running Ubuntu 10.04 only on my pc, will it be an issue? I am just guessing that it is easier to do with Windows, but not sure though.

> 
Regarding grounding, have a look at this page it might explain things better than I do: [https://en.wikipedia.org/wiki/Antistatic_wrist_strap](https://en.wikipedia.org/wiki/Antistatic_wrist_strap)


Thanks for the link will read it ASAP. Thanks indeed for the help you have provided to me. It is really heart-warming to see people like yourself helping out total stranges on this very forum. Hats off to you.

---

### Post by MartijnNL on 2011-12-14
The E5700 is not listed in the link you posted to your motherboard info, on the CPU Support tab, so I'm not sure your CPU is actually supported. Where did you get the info that it is? Also it does mention on top of that page that updating the BIOS is necessary before changing CPU's.

Nevertheless, I found instructions for updating the BIOS from USB or Floppy.

Go to the Manual tab, download the ZIP file and open the IG31C-M7S_080425.pdf file which is in the ZIP. You can find the instructions for updating the BIOS on page 24.

You will need to go to the BIOS tab to download the most up to date BIOS. (The top file). I notice there a second file which is described as "Fix OC fail show incorrectly in POST". Which seems to be related to your case. But as the BIOS upgrade above is newer than this fix, I would start with just that.

Perhaps the default settings for the new BIOS will work with your CPU. But as I said in the beginning: it seems that your CPU is not supported. At least, it's not listed. But try the BIOS upgrade anyway. You never know.

---

### Post by asvestomix on 2011-12-14
i agree with that, the bios update may fix the problem on it's own and saves you from the trouble. IF it does not fix the issue then make sure that the cpu is running at the correct speed and also make sure that the core voltage is correct, this [link]("http://ark.intel.com/products/42801/Intel-Pentium-Processor-E5700-%282M-Cache-3_00-GHz-800-MHz-FSB%29") should help abit. It also happens some times that the fsb of the new cpu to be higher than that the memory was running before so if your motherboard run an synchronized speed you may have to fix it manually

---

### Post by pretty_whistle on 2011-12-14
> **MartijnNL said:**
> The motherboard mount posts are the metal parts which are screwed onto the back panel of your computer. Then the motherboard is screwed on top of these posts. They keep the motherboard away from the panel to prevent electrical shortcuts.

I'm not sure that's the cause of your problem though. It looks a bit like this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706924](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706924)

But it might be worth the effort it to check whether all the hardware is properly connected (including these mount posts). Just be careful not to damage your motherboard or memory. Especially be consious of the risk of an electro static discharge. (Either touch something grounded before handling the motherboard, or use an Electro Static Discharge wristband and attach that to something grounded.)
About the bug report you mentioned.  It says:
> 
[Launchpad Janitor (janitor)]("https://launchpad.net/%7Ejanitor")             wrote             on 2011-04-29:                                                            [ #6]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706924/comments/6")                                                        [Expired for linux (Ubuntu) because there has been no activity for 60 days.]

        


---

### Post by tech291083 on 2011-12-15
> **MartijnNL said:**
> The E5700 is not listed in the link you posted to your motherboard info, on the CPU Support tab, so I'm not sure your CPU is actually supported. Where did you get the info that it is?


Yes, I agree with you. I have a friend who is a hardware and he uses the same set of components for his system, ie the same motherboard, memory, CPU. His system has been running quite well without any problems whatsoever and he was the one who built my system. so I got the confirmation from him that my CPU is also supported.

> 
 Also it does mention on top of that page that updating the BIOS is necessary before changing CPU's.
I will try to update the BIOS.

> 
Go to the Manual tab, download the ZIP file and open the IG31C-M7S_080425.pdf file which is in the ZIP. You can find the instructions for updating the BIOS on page 24.
thanks for the exact info, appreciated.

You will need to go to the BIOS tab to download the most up to date BIOS. (The top file). I notice there a second file which is described as "Fix OC fail show incorrectly in POST". Which seems to be related to your case. But as the BIOS upgrade above is newer than this fix, I would start with just that.

> 
Perhaps the default settings for the new BIOS will work with your CPU. But as I said in the beginning: it seems that your CPU is not supported. At least, it's not listed. But try the BIOS upgrade anyway. You never know.

Yes, this is what I think as well. Hopefully the default settings will take care of the problem. Thanks a lot for the reply. It is quite useful.

---

### Post by MartijnNL on 2011-12-15
Good, less us know if it works. And if so, please mark the thread as solved using the thread tools.

---

