---
title: "Could not update ICEauthority file - problem"
date: 2010-03-16
forum: General Help
---

### Post by cheinze5719 on 2010-03-16
Let me start off by saying I'm very new when it comes to anything Linux. Everything was working perfectly until last night when I restarted my computer. (which is running 9.10) Everything appears to boot up normally but right before it gets to the log in screen I get three windows that pop up informing me of errors.

The first one says:
> Could not update ICEauthority file /home/username/.ICEauthority

After I click ok I get a second error:
> There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

And once I click ok and that one I get a third window:
> Nautilus could not create the following required folders:
/home/username/Desktop, /home/username/.nautilus
Before running Nautilus, please correct these folders, or set permissions such that Nautilus can create them.

The only thing I've changed on my computer is I set it up to auto-login, not sure if that helps or not.

If someone could please help me it would be much appreciated!

---

### Post by cheinze5719 on 2010-03-16
Found a fix. I've seen a lot of people with the same or a similar problem so I'm not sure if this is a bug or what but I'll post my solution anyways. After my computer had told me about the errors I entered a terminal with Ctrl+Alt+F2. 

I then typed in:
sudo service gdm restart

This opened up my desktop with everything appearing to be completely normal. I then turned off auto-login and restarted my computer. Once it got past BIOS is ran a bunch or error checks and then allowed my to enter my username and password and it worked.

Like I said I have no idea if this is a bug or not and needs to be reported but I have seen others with similar situations and I hope this helps!

---

### Post by Berable on 2010-03-28
For me doesn't work this!

I continue with the same problem!

My headache is that my home folder is encrypted.

And I'm afraid with this issue because I'm read a lot of posts in this forum 
that the community coudn't  help users, and some people I prefered to reinstall
the system....

I tried about six different solution but until now any of these work's for me

I'll try to post this question in others forum services.


:confused:

](*,)

:frown:

---

### Post by Berable on 2010-03-28
I solved this issue with information in others post

I'll post a new thread with the solution.

---

### Post by tpost001 on 2010-03-29
I get the same 2 first error messages.  After the "There is a problem with the configuration server" error, my screen has a orange and brown desktop (not mine) and just the arrow from the mouse.  No icons, no panels, nada.  I can only do two things.  1) CTRL-ALT-DEL gets me a "Shut Down the Computer" window with 4 options.  2) CTRL-ALT-F1 gets me a terminal like window but just text mode (no scroll bars).  I tried gdm stop and service gdm restart, but I just get back into the Log-in screen and repeat the process.

Here is what I did prior to all of this and this may help someone understand what I need to do to recover from all of this.

I was running 9.10 version -20 and S.M.A.R.T. told me that I was having problems with my hard drive (bad sectors and the number of sectors was growing with every reboot).  I did a dd of all partitions to a big external backup drive.  I also copied all of /home to a directory there, too.  In this way I was hoping to keep my Windows XP working, too.  I took my Acer Aspire One completely apart and replaced the existing 120 GB drive with a new 240 GB drive.  Same brand as was installed (Seagate Momentus) but a bigger drive.  I created the partitions and allowed for a slightly larger Windows partition (20 GB instead of 15 GB).  I kept the Ubuntu partition at 15 GB. After transferring the rescue and Windows partition over, I copied my /home backup to the /home mount point.  THEN I installed Ubuntu 9.10 from a live CD.  I used a USB DVD drive as the AAO does not have one.  Everything appeared to go well.  No error messages.  I then tried Windows first, and after the initial boot screen, it switches video modes and all I get is a Windows background and the Windows logo and then it stops doing anything.  Likewise, I start Ubuntu 9.10.  I got the same first two errors as mentioned above, and nothing.

I was able to eliminate the first error by chown user:user /home/user/.ICEauthority.  But the next one does not go away.

Is it possible that because the live CD iso that I pulled off of Ubunutu is 9.10 version -14 and I had -20 there before causing the problems?  Any help would be greatly appreciated.

---

### Post by brunog on 2010-04-03
Thank you for posting the solution.
I had th same problem and your solution helped me to set my login back to normal.
Hope they fix the auto login soon.
Cheers

---

### Post by Flos Headford on 2010-04-08
[FONT="Times New Roman"]With much gratitude to all those who work so hard to help us tyros through the early stages, I'd like to post a method which worked for me, when all else had failed.
Use an Ubuntu distribution disc to get a command prompt.
I then got permissions corrected on my $HOME directory, and made sure I could open all directories with ls commands. Then I tried
```
dpkg
sudo apt-get remove nautilus
shutdown -r now
```
Get back to a CLI by the previous method, and use
```
sudo apt-get install nautilus
sudo shutdown -r now
```
and get the CD out quickly. On restart, I get a clean boot and login.
I hope this as of some help to someone as desperate as I was.
Best wishes,
Phil[/FONT]

---

### Post by Zeniff on 2010-05-10
My problem was NOT ONLY with ~/.ICEauthority being owned by root, but also that there were two additional ~/.ICEauthority* files created for some reason.

Changing the ownership AND renaming/removing those two new files fixed MY problem:

Something bad obviously happened and I figured an important change must have happened so I checked what was modified in the last 10 minutes:
```

find ~/ -mmin +0 -mmin -10

```I compared the files that showed up with files of the same name on a different, working PC, which had the same OS (Ubuntu 9.10) and also checked their permissions. On the bad PC:
```

ls -la ~/.ICE*
  which gave me something like:
-rw------- 1 root   root      45846 2010-05-08 21:09 /home/myuser/.ICEauthority
-rw-r--r-- 2 myuser myuser        0 2010-05-10 13:28 /home/myuser/.ICEauthority-c
-rw-r--r-- 2 myuser myuser        0 2010-05-10 13:28 /home/myuser/.ICEauthority-l

```Only the problem PC had the 2 extra (empty) files compared to the working one:
~/.ICEauthority-c and ~/.ICEauthority-l
Also, the ~/.ICEauthority file was owned by root only on the bad PC.

I changed the ownership to match the working PC and renamed the 2 strange new files:
```

mv -iv ~/.ICEauthority-c ~/.ICEauthority-c.backup
mv -iv ~/.ICEauthority-l ~/.ICEauthority-l.backup
sudo chown myusername:myusername ~/.ICE*

```After that, I didn't get the error anymore. Although I still don't really know what those files were for, I wonder if they were "stale locks" for ICE Authority.

In my case, both times I had this problem I think I was messing with opening extra displays on the same PC using the commands "xinit" and "ssh" (also, "xpra" and "screen" may have done something too, but I'm not sure). I think this is why my problem differed from others'.

Anyway, hope this helps someone. Have a great day! ^^/

---

### Post by oziemike on 2010-06-16
This was a lifesaver. Thanks and it worked!!

Mike

> **cheinze5719 said:**
> Found a fix. I've seen a lot of people with the same or a similar problem so I'm not sure if this is a bug or what but I'll post my solution anyways. After my computer had told me about the errors I entered a terminal with Ctrl+Alt+F2. 

I then typed in:
sudo service gdm restart

This opened up my desktop with everything appearing to be completely normal. I then turned off auto-login and restarted my computer. Once it got past BIOS is ran a bunch or error checks and then allowed my to enter my username and password and it worked.

Like I said I have no idea if this is a bug or not and needs to be reported but I have seen others with similar situations and I hope this helps!

---

### Post by jcwx86 on 2011-04-02
I resolved this problem by changing permissions for my home directory. It turned out the folder /home/james had only rw------- permissions, whilst other users had rwxr-xr-x. To change the permissions to match these I did the following:
```
chmod o+rx /home/james
chmod g+rx /home/james
chmod +x /home/james
```This resolved the issue for me. The other methods, such as changing the permissions on my .ICEauthority file had no effect in my case.

I hope this helps!

---

