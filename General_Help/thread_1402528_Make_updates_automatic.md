---
title: "Make updates automatic?"
date: 2010-02-09
forum: General Help
---

### Post by QwUo173Hy on 2010-02-09
My parents have returned from a months holiday with their Ubuntu laptop. I'm a little shocked to find that the system hasn't updated in all of that time. 

They were online ocassionally and I would have expected the system to at least prompt them to update.

Personally, I have some sort of compulsion to check for updates regularly so I've never experience how the system behaves when left to it's own devices.

How do updates work in Ubuntu and how automatic can I make them?

---

### Post by stoneage on 2010-02-09
System -> Administration -> Software Sources -> Updates -> Automatic Updates

---

### Post by inameiname on 2010-02-09
Unfortunately, that only installs the security updates from the official repositories, not any of the recommended ones, nor those from repositories you've added yourself, such as Pidgin's, Remastersys, any of the PPAs from Launchpad, etc. 

I have looked around for this myself and have yet to find a solid solution that automatically updates any and all updates from the repositories I have on my sources.list. Basically to make it like Windows Auto Updates would be nice. 

Also, I have found that if you tweak '10periodic' and '50unattended-upgrades' in the dir /etc/apt/apt.conf.d and ensure unattended-upgrades is installed you can specify which will automatically get installed and which won't. 

Currently, my '10-periodic' includes at bottom: 'Unattended-Upgrade "1"' in the APT :: Periodic section
and my '50unattended-upgrades' includes (but have yet to figure out how to add PPAs repos here):
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu karmic-security";
        "Ubuntu karmic-main";
        "Ubuntu karmic-universe";
        "Ubuntu karmic-updates";
        "Ubuntu karmic-restricted";
        "Ubuntu karmic-multiverse";

---

### Post by hwttdz on 2010-02-09
I actually just made it a cron job (yes this means I had to make a change to the sudoers file, yes I know this is insecure, yes I know the world will be coming to an end, but at least my machine will be up to date when it happens and I don't have to babysit it).

---

### Post by inameiname on 2010-02-10
Hmmm, interesting idea. Hey whatever works for ya. :)

---

### Post by QwUo173Hy on 2010-02-10
Hmm, thanks guys. inameiname, I'll look in to that. I'd be happy if they were even prompted to install the updates, but it seems there is no alert that your system needs updating.

---

### Post by inameiname on 2010-02-10
Oh, if that's the least that you want, then I believe what I mentioned above should do that, give you a prompted popping up saying to hit 'Install'. At least that's what happens on mine with the above settings.

---

### Post by QwUo173Hy on 2010-02-10
Excellent - happy days!

---

