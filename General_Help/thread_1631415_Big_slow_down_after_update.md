---
title: "Big slow down after update"
date: 2010-11-26
forum: General Help
---

### Post by Alienne on 2010-11-26
Hello.
I would like to ask for your help. I have Ubuntu Lucid Lynx since it came out, and until now it worked fine. I am updating regularly. Today too, I installed everything offered to me by updates manager (I looked through the list and didnt see anything I wouldnt want to update, but I dont remember everything that was there), and it asked for restart. Ok, so I restarted. Everything seemed fine. Then I tried to look at a picture, in normal,default viewer, an huh. It took 3 seconds for the mouse to select the pic, then another about 6 to open the viewer (and we are talking about a 40 KB pic). That was slow, but I thought maybe it was an accident. But no, everything I tried since goes slowly, at about a quarter of speed as before the update. I tried to remove unnecessary things with apt-get autoremove, I tried to stop or end all processes that seemed unnecessary, with no result. I restarted thrice. Nothing comes to mind anymore. 

Does anybody have any idea what could have happened? 

Consider me a newbie, and talk to me in that way, please. If you need more info about my notebook, just ask. Thanks.

---

### Post by ivarn on 2010-11-26
The well known kernel bug again. here's the fix.
Oh, and before you do this you should remove the older kernels.

[SIZE=1]Add this to your /etc/rc.local file (sudo gedit /etc/rc.local)
Code:
mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

and make it executable[/SIZE] [SIZE=1]
Code:
sudo chmod +x /etc/rc.local

And then add the following to your ~/.bashrc file (to open it: gedit ~/.bashrc):[/SIZE] [SIZE=1]
Code:
if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

Run the following command:[/SIZE] [SIZE=1]
Code:
sudo gedit /usr/local/sbin/cgroup_clean

And paste this:[/SIZE] [SIZE=1]
Code:
#!/bin/sh
rmdir /dev/cgroup/cpu/$*

then save the file and make it executable:[/SIZE] [SIZE=1]
Code:
sudo chmod +x /usr/local/sbin/cgroup_clean

And finally, restart the computer or manually run the /etc/rc.local file ("sudo /etc/rc.local").[/SIZE] [SIZE=1]
[/SIZE]

---

### Post by Alienne on 2010-11-27
Thank you. It helped some, so I am marking this thread solved, even though the performance of my comp still isnt as good as it was with the previous kernel. Does this solution works always when the new kernel causes slow down?

---

### Post by phyzzy2008 on 2011-01-05
Which kernel update was this exactly?

---

