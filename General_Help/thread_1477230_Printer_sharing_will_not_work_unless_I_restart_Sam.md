---
title: "Printer sharing will not work unless I restart Samba"
date: 2010-05-08
forum: General Help
---

### Post by scweston on 2010-05-08
Hi all,

I have have recently installed Ubuntu 10.04 on my desktop pc and set-up a shared folder and a shared printer from the Ubuntu desktop.

My shared folder works completely fine and is easily accessible by my windows xp laptop. My printer sharing initially worked fine and I was able to connect and print from the windows xp laptop.

Unfortunately, after a reboot of the ubuntu computer the printer is no longer found by the laptop (the shared folder, however, still works fine). I can get the shared printer working again by using the following command to restart Samba: -

sudo service smbd restart

After restarting Samba, suddenly my laptop can see the printer again.

I don't particularly want to have to restart Samba every time I boot up my computer, so can anybody suggest how to fix this issue?

I understand I could probably make a script that would restart Samba automatically after booting or logging in, but I would rather fix the actual problem than use a workaround like that.

Any help would be much appreciated.
Stephen

---

### Post by cheapsk8 on 2010-05-08
How did you get printer sharing to work to begin with? I am having trouble with this.

I have already resigned myself to the idea of running a script at login to get everything working. As you imply, not a very elegant solution, but I'll take it if it works.

---

### Post by scweston on 2010-05-09
Hi Cheapsk8,

To get my printers setup and shared in the first place I installed the printers using turboprint (a piece of commercial software with more advanced drivers and features that cover a greater range of printers). I then sorted out the sharing by going to System>Administration>Printing, then in the Server menu clicked on Settings and made sure there was a tick by 'Publish Shared Printers Connected to this System'. I then right clicked on the icon for the printer I wanted to share and selected Policies in the window that came up. I made sure there was a tick next to the 'Shared' option. I closed all the windows and checked to see if the printer could be found by my windows xp laptop (which it could)

Unfortunately that only works until I next reboot the machine, then as I said I have to restart Samba to get the printer sharing working again. I have to do this on every reboot of my machine.

Hope this helps Cheapsk8, but also if anybody else know what's actually causing the problem or knows how to fix it, then please let me know!

Stephen

---

### Post by Focke on 2010-06-14
I am having the same issue. Ran into it last week trying to share a printer from a 10.4 machine to a windows 7 laptop. Installed the printer on the Ubuntu machine and set up the share. Was able to see it from the Windows 7 machine and print. Once i restarted the ubuntu machine the share died until i manually restarted samba. I tried adding the restart to rs.local, as a friend reccomended, but that did not work.

---

### Post by scweston on 2010-06-14
Hi,

Thanks Focke. I was beginning to think I was the only person with this issue, but thankfully not. I still haven't fixed this and still have to manually restart samba in the terminal to get printer sharing working properly after every reboot.

Does anyone have any suggestions? I'd much rather fix the underlying problem than have to run scripts at every start-up to sort this.

Stephen

Just to note below is the command I type in the terminal to make my shared printers suddenly appear on my windows laptop.

```
sudo service smbd restart
```

---

### Post by manfaat on 2010-06-15
solution that works for me:

editing the last line in my /etc/init/smbd.conf

that is change &quot;exec smbd -F&quot; to &quot;exec smbd -D&quot;

(but i don't know whether there are any bad consequences from this  change or not. all i know is that &quot;exec smbd -D&quot; is the default command  actually run if we start smbd from terminal)

edited:
i think my problem come from bad compiling or upgrading. command sudo  service smbd restart doesn't work, instead my command is sudo smbd  restart or sudo start smbd (i've forgoten). upter fresh installing my  laptop i don't need to do that change and my samba work well. And the  command to restart is sudo service smbd restart.

---

### Post by scweston on 2010-06-15
Thank you manfaat for your suggestion. I tried this and unfortunately this did not work for me. In fact that modification to /etc/init/smdb.conf seemed to make things worse as not only did printer sharing not work, but then the 'sudo service smbd restart' command I used to manually fix the problem wouldn't work either.

I appreciate your help though and if you have any more thoughts on how this could be fixed I'd love to hear them.

Stephen

---

### Post by scweston on 2010-06-19
Hi all,

Thought I should just end this thread now that I've actually managed to find a satisfactory workaround for my problem.

After much messing around I came to the conclusion the problem was a result of the bug reported below: -

[https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141](https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141)

It seems that Samba starts before CUPS has been started during the boot process whereas it should start after.

I followed the suggestion from Francesco Pretto to put:

sleep 10

just after "pre start script" in /etc/init/smbd.conf & /etc/init/smbd.conf


I hope this helps anyone else who was having a similar issue and didn't know how to fix it.

Stephen

---

### Post by halok on 2010-08-10
> **scweston said:**
> 
I hope this helps anyone else who was having a similar issue and didn't know how to fix it.


THANK YOU!! I was also having the same problem, been looking for a solution all morning, and the problem was as i expected..

Again, Thankyou

---

### Post by peterthevicar on 2010-08-24
Thank you scweston, the fix at [https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141](https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141) #18 worked for me. :D

(note the name of the file is /etc/init/smbd.conf, not smb.conf as stated there)

---

