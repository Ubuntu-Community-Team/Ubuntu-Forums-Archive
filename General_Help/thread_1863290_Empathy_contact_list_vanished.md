---
title: "Empathy contact list vanished"
date: 2011-10-17
forum: General Help
---

### Post by philmjones on 2011-10-17
Hi,

I've been using Empathy for Google chat without trouble for a few weeks, but recently my contact list started performing a Houdini act. I'm still online, and when I add chats manually (CTRL+N) I can type in a contact's email address and begin chatting to them. I've searched here and Google and can't find a solution, just lots of people with the same problem. I'm using Lucid 64-bit with Empathy from the repositories.

I've tried:

[LIST]
[*]Deleting and adding my Google chat account.
[*]Selecting the SSL connection to Google Servers (using 'old SSL' and the correct port)
[*]Deleting (purging) empathy and re-installing.
[/LIST]
All to no avail. Does anyone have any suggestions? Thanks for any help you can offer.

---

### Post by mjuhasz on 2011-10-17
This happened to me on 3 Lucid hosts. Considering the fact that Natty and Oneiric were unaffected I figured empathy (actually telepathy) may be getting old. Something might have changed on the server side because empathy on all Lucid hosts stopped working on the very same day.

Updating my lucid hosts from this ppa brought back everything to normal: [https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)

---

### Post by philmjones on 2011-10-17
Thanks for your suggestion. I added the repository from Launchpad, updated and upgraded (which I assume updated Empathy) and logged out but still have the same version and settings (and same absent contacts). Have I missed something obvious?

---

### Post by mjuhasz on 2011-10-17
Empathy itself will not be updated since it's a frontend only. GTalk support comes from telepathy-gabble so make sure that you have the version 0.9.15-1~ppa10.04+1 after the update and then restart your computer (just in case).

---

### Post by philmjones on 2011-10-18
Thanks for the tip, it worked: contact list restored!

---

### Post by r_howie on 2011-10-20
That fixed the problem for me, too.

Instructions on how to add that PPA repository and update Empathy/Telepathy are here:
[http://www.techdrivein.com/2010/06/install-latest-empathy-in-ubuntu-from.html](http://www.techdrivein.com/2010/06/install-latest-empathy-in-ubuntu-from.html)

---

