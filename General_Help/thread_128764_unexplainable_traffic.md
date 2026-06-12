---
title: "unexplainable traffic"
date: 2006-02-12
forum: General Help
---

### Post by louis_nichols on 2006-02-12
Hi guys! I have a desklet that shows me network traffic and lately it's been showing me constant incoming traffic at a speed my internet connection doesn't even have usually. Needless to say, this happens even when all my internet applications are closed. Is there a way I can find out what is happening? Such as seeing traffic speed per app or port or something?

I have direct internet connection via ethernet, on which I have configured 2 connections: eth0 and eth0:0, the latter for direct connect and the like. I thought, since the speed is unusually high, that it might be traffic on the private IP, but it will stilll be there if I deactivate eth0:0. I must admit networking still has many unknowns for me, so what's happening might be normal, but I would really like to know why this is happening. Also because, having this constant traffic makes speed monitoring apps (like my desklet) kinda useless.

Edit: typos corrections.

---

### Post by njzillest on 2006-02-12
wow this sounds weird...



i had a problem with that. but it was via my wireless. I was pinging so much that i couldnt handle the traffic. All i did was buy a new router.

you can try to check whos pinging with you by going to applications-systemtools-network tools. 


also to see whos been logging into your computer (it may be a hack attack) go to applications-system tools- system log

also you can try to enable fireststarter or ip tables to block whos pinging with you. You can get firestarter via automatix or i think synaptic.



i hope this helped...

---

### Post by louis_nichols on 2006-02-12
thanks for the infos! I do have firestarter installed. i 'm using a blocking by default policy and enabled only services which I really use. I think I can count them on my fingers. I hope I've done things right from this point of view.

I tried using network-tools, but wasn't able to find a tool that shows who's pinging me. Firestarter shows incoming events, but most don't make sense to me. Also, i tried using gnome-system-log, but for some reason it doesn't start anymore. Started from terminal, it just hangs. Nothing happens. Now I'm looking for the log in var/log but as yet I haven't found the one that shows logins.

I must admit that I have had the feeling lately that I'm being hacked, although it miht just be paranoia. What happened was that I was typing "users" in console and it would show more instances of my user than I could account for. For example, I would not log in through gdm, but going to tty1 and logging in and then typing "users"  I would get 2 instances.

But... who'd wanna hack me? lol

---

### Post by louis_nichols on 2006-02-12
Can anyone tell me how I can discover wether someone is trying to hack me? I had a lok over the logs, but... I don't know what to look for.

It says that all logins came from localhost... I think...

---

### Post by newuser111 on 2006-02-12
about being hacked, it depends are you running any server? if you arent, then nothing to worry about, but if you are, theres always the possibility

try installing bastille from the repos, it can really lock down your computer if you are worried about being hacked

pretty easy to use too, had to install a perl library to get it to work though

there is also tiger in the repos which will generate a security report of your computer

---

### Post by louis_nichols on 2006-02-12
thanks! those are reassurring words. :)

I'm not running a server, nor do I know of a reason why someone would want to hack my pc... but... I don't know... why can one be so sure that, if they're not running a server, noone will try to hack them?

I'll check those apps out.

---

### Post by newuser111 on 2006-02-12
because if you are running a server it allows incoming connections or logins

ftp, and telnet servers are risky, ssh can be risky if its not setup properly

---

### Post by louis_nichols on 2006-02-13
Oh... I never thought of it that way. :) thx

---

### Post by louis_nichols on 2006-02-13
You know, sometimes, I just want to give up! I feel so helpless and there's so much to learn that I don't have time to...

For example, I just tried tiger and tried to go through the output but I can't make sense of what it says. It's soooooo much!! :(

---

### Post by njzillest on 2006-02-13
dont worry man im going crazy hear tring to install stuff.. im treing to create a virtuall server... omfg it was so easy to make it on windows.. but ubuntu is living hell!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by louis_nichols on 2006-02-14
well... at least you're trying to install a server... I'm just trying to show how viable Linux is as a desktop OS, both to myself and to others. I just wanna use some office apps, have multimedia, web apps... you know.

but sometimes it's hard.

---

