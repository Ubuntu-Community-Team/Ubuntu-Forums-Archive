---
title: "Problem installing Opera from repositories"
date: 2011-04-30
forum: General Help
---

### Post by A Traveller on 2011-04-30
Hi All.

At the following link, the instructions do not state clearly what is to be entered where and in which order, but here is what I have done after some trial and error:-

[https://help.ubuntu.com/community/OperaBrowser?highlight=%28\bCategoryInstallation\b%29](https://help.ubuntu.com/community/OperaBrowser?highlight=%28\bCategoryInstallation\b%29)

1. IN THE TERMINAL, enter wget -qO - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -

(press Enter)

THEN:-

2. System - Administration - Software Sources.
3. Click on the 'Other Software' tab.
3. Click the 'Add' button.
5. Copy and paste deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free in the APT Line.
6. Click 'Add Source'.
7. Click 'Close'.
8. Click 'Reload'.

THEN BACK IN THE TERMINAL:-

9. Enter sudo apt-get update

(press Enter)

10. Enter sudo apt-get install opera

(press Enter)

My question is, the article also makes it seem as if Installing via repository is different to Installing via shell. Is this correct or is installing via shell just  additional steps required as part of the installation from repository?

Thanks for any clarification. (The Opera icon has appeared in my menus, however, I just wanted to check if I've done it the recommended way.)

---

### Post by Irony on 2011-04-30
The link also says;

```
wget -qO - http://deb.opera.com/archive.key | sudo apt-key add -
```

(If you get "The following packages cannot be authenticated" warnings, you'll also need this:)

```
sudo apt-get install debian-archive-keyring
```

which you don't appear to have done.

---

### Post by A Traveller on 2011-04-30
Hi Irony, thanks for your reply.

I did not get any "The following packages cannot be authenticated" warnings, so I skipped the 'sudo apt-get install debian-archive-keyring'.

I got an error stating that the PUBKEY wasn't available or something, but that was before I figured out that I needed to do step 1 in my original post before anything else, which wasn't the order in which the instructions put it, so I was confused.

Anyhow, Opera seems to have been installed and working from the steps I did take.

Thanks.

---

### Post by Irony on 2011-05-01
> **A Traveller said:**
> My question is, the article also makes it seem as if Installing via repository is different to Installing via shell. Is this correct or is installing via shell just  additional steps required as part of the installation from repository?
Not sure what you mean but synaptic is just a graphical front end for apt. You can add the repository via terminal and install via terminal or do it graphically via synaptic - the instructions are often via terminal because it is easier than posting pictures of the graphical method.

---

### Post by A Traveller on 2011-05-07
Ok, thanks Irony. Seems to be working but not as fast as Firefox.

---

