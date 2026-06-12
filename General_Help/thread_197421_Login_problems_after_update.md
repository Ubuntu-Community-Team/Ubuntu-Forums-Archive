---
title: "Login problems after update"
date: 2006-06-15
forum: General Help
---

### Post by ahaslam on 2006-06-15
Hello,

I have just installed about 60 updates that were issued by Update Manager.
A reboot was required after installation and I was met with a surprise. Once the boot/up-splash had finished a small, ugly box was displayed in center screen. It read, "Automatic login (ahaslam)" and then prompted for my password. It did let me log in, but it's not exactly 'automatic' is it!

How can we fix this and make the log-in process 'automatic'? I've attached screens of some of my login settings:

[ATTACH]11288[/ATTACH]          [ATTACH]11289[/ATTACH]

Thank you,
Tony.

---

### Post by u.b.u.n.t.u on 2006-06-15
I have the same setting as both your images.

When I start my computer it logs in to the desktop like XP does.

The only time I have to give a password is when I sudo or want to make system changes.

I have 44.5MB of updates waiting me. I will install them and see if that corrupts my automatic login.

---

### Post by ahaslam on 2006-06-15
[QUOTE=u.b.u.n.t.u]I have the same setting as both your images.
I have 44.5MB of updates waiting me. I will install them and see if that corrupts my automatic login.[/QUOTE]
Good look, I hope it goes well for you. Little things like that can become quite annoying.
Let us know how it goes.

---

### Post by bollix47 on 2006-06-15
Same problem here after latest updates.

No more 'automatic' login.  Requires password.

Tried using previous image (23) where it used to work but now it doesn't work either.

---

### Post by u.b.u.n.t.u on 2006-06-15
My system is completely up to date. just rebooted and it went straight to my desktop.

Like I said, my settings are identical to yours.

I have no idea why your settings aren't working. Maybe you had something different installed.

I had some kernal files, Thunderbird and Nividia drivers.

I can only suggest the obvious. Change the setting back to no automatic login, then reboot and then change it to automatic login and then reboot.

It is a weird problem.

---

### Post by u.b.u.n.t.u on 2006-06-15
[QUOTE=Anthony Haslam]Good look, I hope it goes well for you. Little things like that can become quite annoying.
Let us know how it goes.[/QUOTE]

By the way, nice desktop!

[http://ubuntuforums.org/gallery/showimage.php?i=2833&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=2833&original=1&c=2)

---

### Post by caldevil on 2006-06-15
To confirm, I am having the same problem.

---

### Post by wubunty on 2006-06-15
Same here.
Annoying small password asking box appears.

---

### Post by bollix47 on 2006-06-15
I was able to get automatic login working again by using the hack mentioned [here]("http://ubuntuforums.org/showpost.php?p=1015911&postcount=13").

The "sudo sed .... " part didn't work for me (said permission denied) so I used sudo gedit /etc/pam.d/gdm and added 

auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user

before @include common-auth directive

Rebooted and was not prompted for password.

I will continue to watch for a better solution but for now this worked for me.

---

### Post by ahaslam on 2006-06-16
[QUOTE=u.b.u.n.t.u]I can only suggest the obvious. Change the setting back to no automatic login, then reboot and then change it to automatic login and then reboot.[/QUOTE]
That was the first thing that I thaught of as well, didn't work though :( 
[QUOTE=u.b.u.n.t.u]By the way, nice desktop!
[http://ubuntuforums.org/gallery/show...original=1&c=2](http://ubuntuforums.org/gallery/show...original=1&c=2)[/QUOTE]
Thanks, I'll be further customising it over the next few weeks, I'll show more screens when I'm done.

---

### Post by ahaslam on 2006-06-16
[QUOTE=bollix47]I was able to get automatic login working again by using the hack mentioned [here]("http://ubuntuforums.org/showpost.php?p=1015911&postcount=13").

The "sudo sed .... " part didn't work for me (said permission denied) so I used sudo gedit /etc/pam.d/gdm and added 

auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user

before @include common-auth directive

Rebooted and was not prompted for password.

I will continue to watch for a better solution but for now this worked for me.[/QUOTE]
Thanks, I'll try that later and let you know how I go.

Tony.

---

### Post by bb002 on 2006-06-16
For anyone that uses my method it will restart Xorg, so your current login session will be lost.
I fixed it by doing alt+ctrl+f1, logging in then
```

sudo /etc/init.d/gdm stop
sudo dpkg -i /var/cache/apt/archives/gdm*2.14.6*.deb
sudo /etc/init.d/gdm start

```

Now I just have to remember not to upgrade gdm until 2.14.8+ comes out. :)


bty did I spell "logging in" right because is doesn't look right. spell check didn't make itself usefully today.

---

### Post by caldevil on 2006-06-16
A fix has been released, we should get it through apt-get soon:
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49964](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49964)

---

### Post by u.b.u.n.t.u on 2006-06-16
[QUOTE=wubunty]Same here.
Annoying small password asking box appears.[/QUOTE]

I got that now too with the latest updates. Well there goes my faith in those responsible knowing what they are doing. 

By the way:
[http://www.ubuntuforums.org/showthread.php?t=197414](http://www.ubuntuforums.org/showthread.php?t=197414)

---

### Post by bruce89 on 2006-06-16
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/+index](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/+index), there is an update to GDM which fixes it - 2.14.9-0ubuntu1.  That is a lot of bugfixes.
EDIT:Oops, I realise now that this has been reported.

---

### Post by ahaslam on 2006-06-16
[QUOTE=bollix47]I was able to get automatic login working again by using the hack mentioned [here]("http://ubuntuforums.org/showpost.php?p=1015911&postcount=13").

The "sudo sed .... " part didn't work for me (said permission denied) so I used sudo gedit /etc/pam.d/gdm and added 

auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user

before @include common-auth directive

Rebooted and was not prompted for password.

I will continue to watch for a better solution but for now this worked for me.[/QUOTE]

Thanks, it worked well.

Will this have any effect upon future GDM updates, such as the fix mentioned by caldevil, along with future versions?

Thanks again, support like that is what makes up for these silly bugs.

Cheers, 
Tony.

---

### Post by bollix47 on 2006-06-16
I can't see it causing a problem in the future but if you're concerned you can replace the new /etc/pam.d/gdm file with the /etc/pam.d/gdm.orig that you created.

I've just updated to the latest version of gdm and replaced my /etc/pam.d/gdm with the original and the problem has been fixed.

---

### Post by ahaslam on 2006-06-16
[QUOTE=u.b.u.n.t.u]I got that now too with the latest updates. Well there goes my faith in those responsible knowing what they are doing. 

By the way:
[http://www.ubuntuforums.org/showthread.php?t=197414](http://www.ubuntuforums.org/showthread.php?t=197414)[/QUOTE]
Don't loose faith (although I too came close). The fix has now been released and available via Update (screwup?) Manager, Synaptic, ect.
If you download the new updates, you won't need to bother with the other avice given on this thread. I have now removed the addition from my 'gdm' file and it's working perfectly.

Let's hope that 'updates' are tested a little more for future releases. Ubuntu has received some harsh reviews regarding its completness & stability, lets not make things worse with buggy updates. ;) 

Tony.

---

### Post by sparkov on 2006-06-28
I'm still having trouble with this problem regardless of having a completely up-to-date system.  I'm still prompted for a password when using auto login, but if I restart gdm:

```
sudo /etc/init.d/gdm restart
```

it logs me in fine without asking for a password.  Why does my system not just do this on startup?

---

