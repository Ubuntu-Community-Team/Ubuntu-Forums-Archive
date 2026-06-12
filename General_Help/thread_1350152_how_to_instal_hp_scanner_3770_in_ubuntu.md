---
title: "how to instal hp scanner 3770 in ubuntu"
date: 2009-12-09
forum: General Help
---

### Post by truefriend on 2009-12-09
Hi
 
I have hp scanner 3770 with me and i am using ubuntu 9.04. now the problm is this that i cant scan any thing cause ubuntu does'nt instal this scanner please if some body have any trick to instal this scanner in ubuntu please share here

---

### Post by ddas4 on 2009-12-09
Search "hp-toolbox" on Synaptic. Install the software - hplip should be installed as a dependency. If not then install, hplip too. 9.04 has xsane installed by default so that will help you view/edit your scans.

---

### Post by truefriend on 2009-12-09
> **ddas4 said:**
> Search "hp-toolbox" on Synaptic. Install the software - hplip should be installed as a dependency. If not then install, hplip too. 9.04 has xsane installed by default so that will help you view/edit your scans.
 
 
will u please define in detail if u dont mind i am new at ubuntu and thnx for reply

---

### Post by ddas4 on 2009-12-12
I am sorry for the late response. This is what you need to do:
Go to GNOME main menu -> then ubuntu software center -> then 'other' category -> type 'hp' in the search box -> select HPLIP toolbox and click on the arrow to the right of the selection -> Say install.

After this installation is done, go to 'graphics' section of ubuntu software center -> search for 'xsane'. If there is green checkbox against 'xsane image scanning program', then it is already installed and you don't need to do anything ; else install xsane as well.

Now you are all set. Go to /usr/share/applications and copy the 'HPLIP Toolbox' shortcut to your panel or desktop.

Double click on this icon to open the app. HPLIP Toolbox will search for your printer ( do keep it turned on ). After a few steps the app would have identified your printer. You should see a 'Scan' option on the default tab of the app (which is the 'Actions' tab). But remember you will see the scan option only if your printer is 'On'. Click on 'Scan' and xsane opens up. You are now ready to scan.

---

### Post by Camilia on 2009-12-12
I go systems > administrative > synaptic package manager and then type in hplip in search.

---

