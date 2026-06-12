---
title: "firefox problems"
date: 2010-06-25
forum: General Help
---

### Post by kduffy101 on 2010-06-25
[CENTER]                 [IMG]http://images2.moneysavingexpert.com/images/forum_style_2/misc/neilsbox_chart.gif[/IMG]              [/CENTER]
                                                           [IMG]http://images2.moneysavingexpert.com/images/forum_style_2/misc/neilsbox_eyes.gif[/IMG] 
                                                                                                                     
                 
             
                                                   
                                                               
                                      
                                  
  []("http://twitter.com/?status=http://forums.moneysavingexpert.com/showthread.php?t=2548075")
             
         
     
                             im new to ubuntu,im just getting used to it,
some times when im on a page(say ebay cars) when i click to open up an  advert the pc goes back to the start page,then when i open up firefox  again i get this message.....Well, this is embarrassing.
Firefox is having trouble recovering your windows and tabs. This is  usually caused by a recently opened web page.  Removing one or more tabs  that you think may be causing the problem.  Starting an entirely new  browsing session.
any ideas on how to fix this?
thanks

---

### Post by kalistona on 2010-06-25
it is not ubuntu but firefox option/addon, mark out the option tweeter, it it the same problem when you open several windows ?
erase tweet (it can come also from option windowslive ? maybe) it is not dangerous because your are not in (no account).
it is only sharing files in contact/adress : useless.

---

### Post by lukashjanssen on 2010-06-25
by the start page do you mean the desktop?

---

### Post by kduffy101 on 2010-06-25
yes it happens when 1 or a few pages open,
yes it takes me back to desk top.

---

### Post by kalistona on 2010-06-25
hackers.

---

### Post by lovinglinux on 2010-06-25
What are those Twitter stuff in your post? If that is not relevant to your problem, please remove. 

You browser is crashing for some reason. Does this happens on specific pages or when viewing any page?

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Post your results.

For more Firefox tweaks and tips see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)
For additional support see [Firefox Optimization and Troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by kduffy101 on 2010-06-25
sorry about the tweeters thing,i copied a question i had posted from another forum about the same problem,
i was directed to here to help sort problem.
before i posted this reply i hit the quick reply+the samething just happened,it took me back to desk top page.

---

### Post by lovinglinux on 2010-06-25
> **kduffy101 said:**
> sorry about the tweeters thing,i copied a question i had posted from another forum about the same problem,
i was directed to here to help sort problem.
before i posted this reply i hit the quick reply+the samething just happened,it took me back to desk top page.

Start Firefox from a terminal and post the errors generated when it crashes.

---

### Post by kduffy101 on 2010-06-25
how do i do that?

---

### Post by Ryan Dwyer on 2010-06-25
I'm going to take a stab in the dark and guess that you have swap disabled. When your memory fills up and you have no swap it will kill whatever process asked for more memory.

Next time it happens, go to Applications > Accessories > Terminal. Type in: tail /var/log/syslog
Copy and paste the output here.

---

### Post by lovinglinux on 2010-06-25
> **kduffy101 said:**
> how do i do that?

Close Firefox, then go to "Applications > Accessories > Terminal", type **firefox** and hit enter.

---

### Post by kduffy101 on 2010-06-25
kevin101@kevin101-desktop:~$ tail /var/log/syslog
Jun 25 12:39:12 kevin101-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 25 12:39:12 kevin101-desktop ntpdate[1268]: adjust time server 91.189.94.4 offset -0.382921 sec
Jun 25 12:39:12 kevin101-desktop pulseaudio[1052]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jun 25 12:39:12 kevin101-desktop pulseaudio[1052]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Jun 25 12:39:12 kevin101-desktop pulseaudio[1052]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jun 25 12:39:14 kevin101-desktop kernel: [   27.712010] eth0: no IPv6 routers present
Jun 25 12:40:11 kevin101-desktop AptDaemon: INFO: Initializing daemon
Jun 25 12:45:12 kevin101-desktop AptDaemon: INFO: Quiting due to inactivity
Jun 25 12:45:12 kevin101-desktop AptDaemon: INFO: Shutdown was requested
Jun 25 13:17:01 kevin101-desktop CRON[1333]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
kevin101@kevin101-desktop:~$

---

### Post by kduffy101 on 2010-06-25
(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1552): Gdk-WARNING **: XID collision, trouble ahead
Segmentation fault
kevin101@kevin101-desktop:~$

---

### Post by kduffy101 on 2010-06-25
anyone got any comments?

---

### Post by lovinglinux on 2010-06-25
> **kduffy101 said:**
> anyone got any comments?

Try to reinstall firefox and create a new user profile. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

