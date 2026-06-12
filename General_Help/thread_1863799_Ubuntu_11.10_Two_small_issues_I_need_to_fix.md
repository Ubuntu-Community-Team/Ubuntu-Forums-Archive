---
title: "Ubuntu 11.10: Two small issues I need to fix"
date: 2011-10-18
forum: General Help
---

### Post by veroslav on 2011-10-18
Hi all,

I've installed Ubuntu 11.10 and I am very satisified so far. I have two issues that I need to resolve though, so here it goes:

1. I've used the gnome-tweak-tool to change the theme from Ambiance to Adwaita, however, the window borders still have Ambiance orange look to them (orange max, min and close buttons and black title bar). I couldn't find any options to change this in gnome-tweak-tool. When using gnome shell, however, the window border IS changed to match Adwaita. How can I change it in Unity as well?

2. I've added a PPA for Ubuntu Tweak and yesterday I was notified that an update to it was available, so I tried to update. However, I've got an error, something like "Requires installation of untrusted packages", and the only option I was given was to accept it (OK). I had to abandon the update. How can I fix this issue?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by hwttdz on 2011-10-18
2) I'd remove the ppa and re-add using 
sudo apt-add-repository ppa:somestuff
where somestuff will be listed on the launchpad ppa site for the package. That will get the key for you.

1) I actually switched to xfce after this update to gnome, I find it more customizable.

---

### Post by veroslav on 2011-10-18
Thank you for your reply.

I re-installed Ubuntu Tweak according to your instructions and it worked pretty well. Now I will have to watch the next update and see if it goes smoothly.

Thanks again!

Regards,
Veroslav

---

### Post by veroslav on 2011-10-21
I just wanted to confirm that the latest update of Ubuntu Tweak installed successfully and it also contained a new feature that enables the user to change a window theme, which I did and it worked beautifully! This solved my first problem above and all is fine.

Thought that it was good to point it out for others who wanted to know.

Kind Regards,
Veroslav

---

