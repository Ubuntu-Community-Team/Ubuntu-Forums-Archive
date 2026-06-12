---
title: "strange internet issue..."
date: 2012-02-25
forum: General Help
---

### Post by imachavel on 2012-02-25
hello, I've recently been having a lot of problems with my at&t 2wire, was having quite a few d.n.s. issues with every single device in the house I wanted to connect with. I called up at&t support, and we did a ton of stuff, one being to enter a new public i.p. address, which finally fixed the problem. But I've having dns issues up the *** while using my d link router to give out dhcp. So I'm using dhcp to connect to a dns server, with a public i.p. address given to the at&t 2wire modem in between right?(You know, I was just thinking about how easy it would be to spoof an i.p. address if you knew how to change your public i.p. on your isp provided modem, of course you wouldn't know how many ipv4s would be left)

These continued dns errors haven't been anything serious, I solve them usually by running an ipconfig /release then ipconfig /renew on my PC with windows, or just restarting the computer. But lately the other PC connected to the network which has Ubuntu installed, it's a dell dimension 4700, hasn't been liking dhconfig -r, or a restart. I'm wondering why it's not liking the i.p. address it's been given. Maybe the i.p. address it's been given isn't working well with the dns configuration of the at&t 2wire modem that it's trying to connect to. I have some config information that I've saved in two text files that I'm going to upload. Do you think I should just disconnect the PC using Ubuntu from the d link router and hard wire it to the at&t 2wire modem? Or use a wireless device(I have one) and use it's ssid to connect to the 2wire modem?

Here is some additional info aside from the uploaded text files:

i.p. address of at&t 2wire modem: 192.168.1.254
i.p. address of d link router: 192.168.0.1

I forget the difference between what arp and netstat lists, so I want even bother, besides I'm not setting up a computer with a dedicated ethernet i/o in the nic as an i.p. configurations server instead of a file server anyway. Any ideas?

---

### Post by imachavel on 2012-02-25
wtf??!?!? Why didn't the files upload? Oh files are invalid, I need to compress them I think. One second

---

### Post by imachavel on 2012-02-25
Ok, can you see the files?? Man, You can't compress files in windows without sending them to a compressed folder? At least not with 7zip you can't. What a pain in the ***, I almost forgot how much I hate winblows

---

