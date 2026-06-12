---
title: "Problems with Unison &amp; SSH"
date: 2009-10-02
forum: General Help
---

### Post by jlacroix on 2009-10-02
I've been having a little problem, though I've been able to work around it regularly and haven't complained much. Now I figured I may as well get this fixed because it's starting to annoy me.

Anyway, I have a desktop computer (jeremy-desktop) and a laptop (jeremy-laptop). Both run 64-bit Kubuntu. I use Unison to sync the two. Basically what I do is work with my laptop during the day, and then sync my laptop to my desktop when I get home at night. This all works well. I also sometimes SSH into my Desktop at home and run updates and things during the day.

What happens is that sometimes this all gets broken out of nowhere. I don't turn jeremy-desktop off at all, it stays on all the time. However, every now and then the IP address will change to something else. In my router (A Linksys WRT54GS2) doesn't have an option to hold on to the IP address for longer than 1 day. It's also not compatible with alternative firmwares such as Tomato as far as I know. When this happens I remote connect to my router, go into port forwarding, and change the forwarding address to whatever the router thinks my IP address should be now.

To rectify this, I have tried to set static IP addresses. That's an easy thing to do in Ubuntu, but not so much in Kubuntu. I cannot get the static IP's to stick, and usually by the time I'm done changing my IP's to static I kill my entire system. So I guess I have the following questions:

1.) Can I somehow make my desktop computer force the router to hold onto the IP address lease?

2.) Or maybe I can somehow get name recognition in Unison so I can direct it to jeremy-desktop instead of to xxx.xxx.xxx.100?

3.) What about remote connecting in SSH, might name recognition work for that?

About every other day I have to log in to my router remotely, find out what the IP address is of my Desktop, and change my Unison profile and Putty commands to reflect the new IP address. I'd rather not go through all of that. :(

---

