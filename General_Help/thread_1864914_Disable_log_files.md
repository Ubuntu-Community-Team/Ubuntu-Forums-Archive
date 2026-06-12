---
title: "Disable log files"
date: 2011-10-19
forum: General Help
---

### Post by chillywillyhoe on 2011-10-19
Im losing all my disk space to log files, my kern.log and syslog.log is usually taking up 10gb of space. anyway to disable logging all together on 11.10

---

### Post by gsmanners on 2011-10-19
I think you should be okay if you just delete the old .gz files (that I doubt you really need). 10 GB? Seriously?

---

### Post by Slim Odds on 2011-10-19
> **chillywillyhoe said:**
> Im losing all my disk space to log files, my kern.log and syslog.log is usually taking up 10gb of space. anyway to disable logging all together on 11.10

How old are those files? If they are really that big, you have problems that you need to deal with (not just disabling the logs).

---

### Post by gmargo on 2011-10-19
You should not disable logging.  

But I'm surprised your log files are that big.  Have you disabled log file rotation?

---

### Post by seawolf167 on 2011-10-19
If you log files are taking up that much space I'd be very surprised if there isn't a error that is reoccurring over and over. Before changing anything I'd *highly *suggest looking through the logs to see what is spamming out error messages.

---

### Post by Slim Odds on 2011-10-19
> **seawolf167 said:**
> If you log files are taking up that much space I'd be very surprised if there isn't a error that is reoccurring over and over. Before changing anything I'd *highly *suggest looking through the logs to see what is spamming out error messages.

My point exactly!

They don't get big for no reason.

---

### Post by chillywillyhoe on 2011-10-19
im not sure if log rotation is working out not but this has happened to me twice, i have only been using ubuntu 2 weeks now, i attempted to open the logs with the text editor, their so big that as its loading them my laptop freezes and i have to turn the power off. if i could find out how to open them to see whats going on i could do that, turning it off would be lazier haha, but everything works fine just after a few days all my space is gone from logs. any help is appreciated. 
also i just rotated the logs manually today, but they are still taking up space

also their 10-15gb each

---

### Post by gsmanners on 2011-10-19
Okay. Well if your logs are taking more than 10MB, you have bigger problems of some kind than just running out of space. You have something in your system (hardware problems or maybe a serious security problem) that desperately needs the attention of a professional. Or you could backup your vital data and reinstall.

---

### Post by chillywillyhoe on 2011-10-19
rotated the logs today and its already at 247mb, in the kern.log i see this error repeating 
"Oct 19 11:37:34 ubuntu kernel: [ 2824.205405] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Oct 19 11:37:34 ubuntu kernel: [ 2824.205424] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Oct 19 11:37:34 ubuntu kernel: [ 2824.205444] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Oct 19 11:37:34 ubuntu kernel: [ 2824.205463]"

The [2911.xxxxxx] changes though.

in the syslog.log 
"Oct 19 11:37:18 ubuntu kernel: [ 2807.779771] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Oct 19 11:37:18 ubuntu kernel: [ 2807.779792] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Oct 19 11:37:18 ubuntu kernel: [ 2807.779812] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times"

so there's my problem, any way to fix that?

---

### Post by gsmanners on 2011-10-19
Okay. That's interesting.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813)

---

### Post by Slim Odds on 2011-10-19
Maybe this will help: [https://bbs.archlinux.org/viewtopic.php?id=114935](https://bbs.archlinux.org/viewtopic.php?id=114935)

---

### Post by chillywillyhoe on 2011-10-19
> **Slim Odds said:**
> Maybe this will help: [https://bbs.archlinux.org/viewtopic.php?id=114935](https://bbs.archlinux.org/viewtopic.php?id=114935)

in the fix on that page i see im suppose to add this
$ cat ~/.drirc 
<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>

but i don't know where to add that exactly

---

### Post by gsmanners on 2011-10-19
```
<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```

Open a text editor and paste that into it. Then save it to a file called .drirc in your home folder (don't forget to include the .)

---

### Post by chillywillyhoe on 2011-10-19
> **gsmanners said:**
> ```
<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```

Open a text editor and paste that into it. Then save it to a file called .drirc in your home folder (don't forget to include the .)

i copied that into a text editor and saved it as ".drirc" in my home folder, going to reboot and see if the errors continue

---

### Post by chillywillyhoe on 2011-10-19
wow and just like that the logs stopped, thank you everybody for your help, im glad i didn't quit and go back to windows.

now how do you rotate the logs properly, i think i did it  cause the 10gb kern.log is gone but but i have one "syslog.1" that's 9.7gb still sitting there

---

### Post by Slim Odds on 2011-10-20
> **chillywillyhoe said:**
> wow and just like that the logs stopped, thank you everybody for your help, im glad i didn't quit and go back to windows.

now how do you rotate the logs properly, i think i did it  cause the 10gb kern.log is gone but but i have one "syslog.1" that's 9.7gb still sitting there

The logs should rotate automatically. There is a daily cron job that does that. You can probably safely delete those huge log files now that you know what the problem was. But that's up to you.

---

### Post by joshwho on 2011-11-24
I have this same exact issue. I tried putting that script in the Home Directory I then restarted and it still happens.  I notice it only happens when my pc idles. Probly When the Screen saver is in use.  It would never do it when i am using it. I also tried putting that script in the etc  and still happens.     I am hoping to just find a way to disable logging.   I know it is a bug problem. I don't really care about my log files.   If my system messes up I just re install it.  I don't lose anything because I keep all my important stuff on my External Drive. Can some one please just point me in the right direction to disable logs.  Or at least disable  kern.log and syslog

If I can do that I would be very Happy with Xubuntu.


Another thing I am not understanding is when I delete the Logs  it doesn't restore my disk space. Where do the files go after i delete them?

---

### Post by joshwho on 2011-11-24
Never Mind I figured it out

I opened Synaptic Package Manager and looked for a program called rsyslog  and removed it.  No more kern.log or syslog filling up my drive any more thank god.

I know removing it is not the best thing but I didn't want to keep reinstalling any more.

This is just a temp removal until the bug is fixed.

So far the only suggestions I found was to just get a new Graphix card which I am not doing because mine works fine.


Happy Thanksgiving  every one.

---

### Post by JoeDesertrat on 2011-12-21
OK, I found a solution to this a few days ago. My kern.log and syslog are now remaining at normal sizes instead of filling up to GB's in size. Unfortunately, I forgot to save the link where the discussion was but here's what I found. Simply create a text file named .drirc in your home directory. The file should contain the following text:


<driconf>
<device screen="0" driver="dri2">
<application name="Default">
<option name="vblank_mode" value="0" />
</application>
</device>
</driconf>

---

