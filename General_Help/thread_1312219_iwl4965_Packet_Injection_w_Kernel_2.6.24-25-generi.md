---
title: "iwl4965 Packet Injection w/ Kernel 2.6.24-25-generic"
date: 2009-11-03
forum: General Help
---

### Post by dominicx1889x on 2009-11-03
Before you sigh and tell me to read other 'solutions' on this website or other forums, there's a few things to know first.
I'm using Hardy Heron and kernel 2.6.24-25-generic.
I have a Intel Wireless 4965 AGN card.
Video card is a nvidia 8700M GT. (Reasonf or listing that).

I have tried almost EVERY possible solution to getting packet injection on this card. I have updated my kernel to 2.6.25 and higher and have followed several instructions. IF I update past 2.6.24 my video card will not work because it is a restricted driver. I've tried multiple methods to get it to work but it refuses to cooperate. I will remain using 2.6.24-25-generic until it can be solved easier.
I use aircrack-ng the NEWEST version, I have installed and patched everything possible for the wireless card itself, even packet injection patches. I was unable to create virtual interfaces until recently (mon0).
Now that I am able to create this other interface to use for packet injection, I run into more problems:
Computer lockups, 'caps-lock error'(caps blinks on/off constantly and computer freezes), running aircrack-ng wlan0 --test and aircrack-ng mon0 --test either locks computer up or comes back finding a few APs but does not send out any packets. (0/30).

YES I have my card in monitor mode everytime, and specific channels on certain occasions. I have done numerous modprobes for the drivers and I've manually entered them to startup for my modules. NOTHING WORKS.

There are times where I try to modprobe and I get 'error inserting' messages, and a few dmesgs.
If I come across those again I will post them.

Any suggestions? I have read too many threads and have been working on this for 2 weeks. Replying with other threads will probably not solve it, I would like to work 1 on 1 with somebody, if you'd like my email let me know.

Thank you

---

### Post by dominicx1889x on 2009-11-03
Before you sigh and tell me to read other 'solutions' on this website or other forums, there's a few things to know first.
I'm using Hardy Heron and kernel 2.6.24-25-generic.
I have a Intel Wireless 4965 AGN card.
Video card is a nvidia 8700M GT. (Reasonf or listing that).

I have tried almost EVERY possible solution to getting packet injection on this card. I have updated my kernel to 2.6.25 and higher and have followed several instructions. IF I update past 2.6.24 my video card will not work because it is a restricted driver. I've tried multiple methods to get it to work but it refuses to cooperate. I will remain using 2.6.24-25-generic until it can be solved easier.
I use aircrack-ng the NEWEST version, I have installed and patched everything possible for the wireless card itself, even packet injection patches. I was unable to create virtual interfaces until recently (mon0).
Now that I am able to create this other interface to use for packet injection, I run into more problems:
Computer lockups, 'caps-lock error'(caps blinks on/off constantly and computer freezes), running aircrack-ng wlan0 --test and aircrack-ng mon0 --test either locks computer up or comes back finding a few APs but does not send out any packets. (0/30).

YES I have my card in monitor mode everytime, and specific channels on certain occasions. I have done numerous modprobes for the drivers and I've manually entered them to startup for my modules. NOTHING WORKS.

There are times where I try to modprobe and I get 'error inserting' messages, and a few dmesgs.
If I come across those again I will post them.

Any suggestions? I have read too many threads and have been working on this for 2 weeks. Replying with other threads will probably not solve it, I would like to work 1 on 1 with somebody, if you'd like my email let me know.

Thank you

---

### Post by dominicx1889x on 2009-11-11
-bump-

---

### Post by dominicx1889x on 2009-11-11
anyone? :(

---

### Post by slakkie on 2009-11-11
If you want 1 on 1 sessions I think irc is the better option.

Channels to try: #ubuntu, and maybe #ubuntu-kernel. I think they should be able to help you.

---

### Post by dominicx1889x on 2009-11-12
Any help would be appreciated.

---

