---
title: "Made an Error with chmod !"
date: 2010-01-18
forum: General Help
---

### Post by Bender_cr on 2010-01-18
Hi Guys I'm a complete n00b on this things I wanted to create an user but don't allow it to see the other user's home folder so I made chmod 0750 /home/folder and it worked fine so I went ahead and decided to completely forbid access to the root folder and I had the "great" idea to make chmod 0750 /, and now I'm having problems with wine and other applications, in example I used to have a folder in this address 209.239.114.51/mmgr but now it's giving me errors and if I try to run some applications I got error "There was an error creating the child process for this terminal", So any help or idea what can I do here.

Thanks



Sorry for my bad english

---

### Post by nothingspecial on 2010-01-18
Have you run chmod -R on /? :shock:

Because if you have ......


...... and I am never one to recommend this when there is a fix ......

....... the easiest option would be to reinstall.

If that`s what you`ve done, you have toasted your installation.

Well done :guitar:, I do it from time to time for fun, but not on my main rig.

---

### Post by synapsys on 2010-01-18
baaaad puddy tat.

---

### Post by nothingspecial on 2010-01-18
Before you do reinstall, post the output of

```
history
```

so we can see what you`ve done and (probably not, but maybe) fix it.

---

### Post by Bender_cr on 2010-01-18
HUmmm Damn I did

```
221  [2010-01-18 14:43:44] sudo chmod 0750 /home/trinity/
  222  [2010-01-18 14:44:56] sudo chmod 0750 /var/
  223  [2010-01-18 14:45:15] sudo chmod 0750 /
  224  [2010-01-18 14:45:58] sudo chmod 0755 /
  225  [2010-01-18 14:48:21] sudo chmod 0750 /etc/mysql/
  226  [2010-01-18 14:51:40] cd
  227  [2010-01-18 14:51:45] cd /home/pruebas/
  228  [2010-01-18 14:51:48] ls
  229  [2010-01-18 14:51:54] hg clone https://trinitycore.googlecode.com/hg/ trinitycore
  230  [2010-01-18 14:52:22] hg
  231  [2010-01-18 15:01:07] sudo hg
  232  [2010-01-18 15:01:15] su hg
  233  [2010-01-18 15:01:18] cd
  234  [2010-01-18 15:01:20] cd trinitycore/
  235  [2010-01-18 15:01:21] hg
  236  [2010-01-18 15:01:24] sudo hg
  237  [2010-01-18 15:01:40] hg
  238  [2010-01-18 15:17:10] ls -ld /home/trinity/
  239  [2010-01-18 15:17:16] ls -ld /var/
  240  [2010-01-18 15:20:05] cd
  241  [2010-01-18 15:20:13] chmod 0750 /home/trinity/
  242  [2010-01-18 15:23:38] hg
  243  [2010-01-18 15:47:25] sudo chmod 666 /dev/null
  244  [2010-01-18 15:47:37] sudo nautilus
  245  [2010-01-18 15:48:42] sudo
  246  [2010-01-18 15:48:44] sudo nautilus
  247  [2010-01-18 15:54:42] history

```and in root user

```
 90  [2010-01-18 14:55:43] hg
   91  [2010-01-18 14:56:05] chmod 0755 / -r
   92  [2010-01-18 14:56:25] sudo chmod 0755 / -r
   93  [2010-01-18 14:56:30] sudo chmod 0755 /
   94  [2010-01-18 14:56:32] cd
   95  [2010-01-18 14:56:34] cd /
   96  [2010-01-18 14:56:39] sudo chmod 0755
   97  [2010-01-18 14:56:45] sudo chmod 0755 /root
   98  [2010-01-18 14:58:06] sudo chmod 0755 /usr/bin/
   99  [2010-01-18 14:59:46] sudo chmod 0755 / -R
  100  [2010-01-18 15:01:38] sudo chmod 0777 /
  101  [2010-01-18 15:01:48] sudo chmod 0777 /usr/bin/
  102  [2010-01-18 15:01:51] sudo chmod 0777 /usr/bin/ -R
  103  [2010-01-18 15:08:17] cd /home/trinity/
  104  [2010-01-18 15:08:19] cd trinitycore/
  105  [2010-01-18 15:08:20] hg
  106  [2010-01-18 15:10:27] cd
  107  [2010-01-18 15:10:39] chmod 0777 /bin/ -R
  108  [2010-01-18 15:12:49] chmod 0777 /var/
  109  [2010-01-18 15:12:58] chmod 0755 /var/
  110  [2010-01-18 15:13:24] chmod 0755 /var/ -R
  111  [2010-01-18 15:13:35] chmod 0777 /var/ -R
  112  [2010-01-18 15:14:49] chmod +x /var/ -R
  113  [2010-01-18 15:16:15] chmod 777 /
  114  [2010-01-18 15:16:27] chmod 777 /var/ -R
  115  [2010-01-18 15:17:36] ls -ld /var/www/
  116  [2010-01-18 15:18:27] cd /
  117  [2010-01-18 15:18:31] chmod ugo+rwx
  118  [2010-01-18 15:18:36] chmod ugo+rwx -R
  119  [2010-01-18 15:18:45] chmod ugo+rwx /var/-R
  120  [2010-01-18 15:18:50] chmod ugo+rwx /var/ -R
  121  [2010-01-18 15:19:05] chmod ugo+rwx /
  122  [2010-01-18 15:19:13] ls -ld /var/www/
  123  [2010-01-18 15:19:19] ls -ld /home/trinity/
  124  [2010-01-18 15:27:50] ls -l /etc/gdm
  125  [2010-01-18 15:28:14] sudo chmod 666 /dev/null
  126  [2010-01-18 15:48:14] chmod 4111 /usr/bin/sudo
  127  [2010-01-18 15:48:39] chmod 777 /var/
  128  [2010-01-18 15:52:08] ls -l usr/bin/sudo
  129  [2010-01-18 15:52:19] chwon root:root /usr/bin/sudo
  130  [2010-01-18 15:52:27] chwon
  131  [2010-01-18 15:52:34] chmod 4755 /usr/bin/sudo
  132  [2010-01-18 15:52:37] ls -l usr/bin/sudo
  133  [2010-01-18 15:53:03] chmod 755 /usr/bin/sudo
  134  [2010-01-18 15:53:06] chmod 755 /
  135  [2010-01-18 15:53:09] chmod 755 / -R
  136  [2010-01-18 15:54:09] history

```

I always cancelled the chmod 0755 and 777 / -R it ran for 3 to 10 seconds

---

### Post by synapsys on 2010-01-18
> **nothingspecial said:**
> so we can see what you`ve done and (probably not, but maybe) fix it.

It can be fixed, but it will be a lot of work, you would have to know the exact permissions of everything in the / folder and change them all by hand.

---

### Post by nothingspecial on 2010-01-18
> **synapsys said:**
> It can be fixed, but it will be a lot of work, you would have to know the exact permissions of everything in the / folder and change them all by hand.

That`s why, for this at least, I recommend a reinstall.

I couldn`t possibly know the permissions and group ownership of every file in Ubuntu.

And reinstalling will take about 15-20 mins, while fixing this may take days.

I take my hat off to you. I break linux for fun but .........

---

### Post by Bender_cr on 2010-01-18
xD Love this forum thanks guys, I'm starting reinstallation right now, hehehe

---

### Post by nothingspecial on 2010-01-18
One day, when my wife and kids are away for a day, I`m going to do this and see if I can fix it.

This is kind of what my sig means. 

Brilliant.

---

### Post by synapsys on 2010-01-18
> **Bender_cr said:**
> xD Love this forum thanks guys, I'm starting reinstallation right now, hehehe


Look into having a seperate / and /home partition, it makes re-installing (and upgrading) a breeze..

[quote=nothingspecial]I`m going to do this and see if I can fix it.[/quote]

Crazy talk!

---

### Post by nothingspecial on 2010-01-18
I have a file of -----no offence Bender-cr------ "really stupid things to do with linux"

This is going top of the list!

It started when I decided to rm everything from a drive and cp the new stuff onto it at the same time. I ended up in a loop, rm was rming what cp was cping. There`s a thread on here about it somewhere.

I absolutely love the fact that you can tell your computer to hose itself and, because it`s linux, it will do it, no questions - that is control.

One day, when it`s comprehensive enough, I`ll post it in the cafe.

---

### Post by synapsys on 2010-01-18
With great power comes great responsibility

---

### Post by Bender_cr on 2010-01-18
hahaha that's cool, at least was a funny stupid thing

---

