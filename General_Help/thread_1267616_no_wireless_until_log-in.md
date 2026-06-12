---
title: "no wireless until log-in"
date: 2009-09-15
forum: General Help
---

### Post by chitowner2 on 2009-09-15
(If the moderator needs to move this, please accept my apologies if I am opening a thread in the wrong place  <g>)

Got a new wireless-N USB dongle yesterday and it is working- sort of.  This is a Rosewill RNX-N1 which supports 802.11N 2.0. I am using it on a jaunty/kde4.2 install and have it working with networkmanager.

Here is my problem: I want wireless connection working *before* login to a user session so ssh access is enabled at an early stage of boot. 

I understand that developer's wouldn't recommend this for security reasons, but let's ignore that for the time being.

Having ssh enabled before login allows a range of troubleshooting options that are not possible otherwise, especially the ability to reboot and re-access the PC via ssh.

Does anyone have a solution to this? Ideally a solution would obviate networkmanager and a wireless connection would be already established when a user logs in, instead of having to go through another set of functions to have it run. networkmanager also 'times out', forcing one to go back and restart the thing again after some period of inactivity. 

Again, I recognize the security aspects of this behavior. I just don't want any of it, so feel free to offer useful ideas without worrying that I'll come back and yell if I encounter security problems from an outside source.

Thanks!
CT

---

### Post by P4man on 2009-09-16
this howto is old, but I think should still work for you:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

if you do that, you should have wifi before logging in. Not that i tried it...

---

### Post by slakkie on 2009-09-16
Posts like this really trigger my documentation finger. I've started writing[1] a networking howto for the wiki to resolve these issues once and for all. 

[SIZE="1"][1] Writing a big word, I'm translating my own Dutch howto to english.[/SIZE]

---

### Post by chitowner2 on 2009-09-16
P4Man: Ill try to take advantage of that link. I'm still a noob with a lot of this stuff even tho I've been using Ubu for a good 3 years now.

---

### Post by chitowner2 on 2009-09-16
slakkie: I sincerely hope you post what you're working on when its done and I *hope* I get my problem fixed before that!!

---

### Post by chitowner2 on 2009-09-16
> **P4man said:**
> this howto is old, but I think should still work for you:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

if you do that, you should have wifi before logging in. Not that i tried it...


OK, the scenario has somewhat degenerated. Last night the Wireless-N was working, this morning it was not. I have tried everything I can think of; deleting and re-doing the connection in knetworkmanager, with appropriate logout/in &/or rebooting. Nothing works to re-establish the wireless connection. 

"iwlist" seems to 'see' the router, but I can not ping from or to the box. I see from iwlist that noise is -71dB but signal is only -66dB with an efficiency of only 43%. Pretty sad. Maybe S/N ratio is the real problem? I have no way of identifying why the noise. Nothing that I am aware of has changed since last night.

---

### Post by slakkie on 2009-09-16
> **chitowner2 said:**
> slakkie: I sincerely hope you post what you're working on when its done and I *hope* I get my problem fixed before that!!

If you speak Dutch you can find it here: [http://wiki.fok.nl/index.php/Dig/linux/wireless](http://wiki.fok.nl/index.php/Dig/linux/wireless) or have a look at the translation. It is somewhat rusty English, but understandable. I'm merging several resources from the wiki while translating the Dutch document. It will take a while, you will be finished quicker :)

---

### Post by slakkie on 2009-09-16
The translation can be found here:
[http://translate.google.nl/translate?hl=nl&sl=nl&tl=en&u=http%3A%2F%2Fwiki.fok.nl%2Findex.php%2FDig%2Flinux%2Fwireless](http://translate.google.nl/translate?hl=nl&sl=nl&tl=en&u=http%3A%2F%2Fwiki.fok.nl%2Findex.php%2FDig%2Flinux%2Fwireless)

---

### Post by chitowner2 on 2009-10-19
update

I upgraded to 4.3 on koala and switched to WICD. After a bit of back-and-forth with the router, I got the wireless-N connected just fine. It starts automatically and connects during boot before login, so it's doing what I wanted.

CT
:guitar:

---

