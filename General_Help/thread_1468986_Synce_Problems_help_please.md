---
title: "Synce Problems help please"
date: 2010-05-01
forum: General Help
---

### Post by khalidabuu on 2010-05-01
Could not display "synce://Touch%20Pro%202/".
Nautilus cannot handle "synce" locations.

I get this when i try and explore the files on my winmo phone using synce tray icon

python-rra:
  Depends: python (<2.6) but 2.6.5-0ubuntu1 is to be installed
python-rapi2:
  Depends: python (<2.6) but 2.6.5-0ubuntu1 is to be installed
python-rtfcomp:
  Depends: python (<2.6) but 2.6.5-0ubuntu1 is to be installed
opensync-plugin-synce:
 Depends: synce-sync-engine but it is not going to be installed
synce-sync-engine:
 Depends: python-rra but it is not going to be installed
 Depends: python-rapi2 but it is not going to be installed
 Depends: python-rtfcomp but it is not going to be installed

these packages are needed to function properly it says they need updating but i cant update or install them it says this for each one.

---

### Post by Ocxic on 2010-05-01
install the packages manually starting from the bottom of your list, and use synaptic to force a package version lower then 2.6 for the top 3 (package menu).

---

### Post by khalidabuu on 2010-05-01
> **Ocxic said:**
> install the packages manually starting from the bottom of your list, and use synaptic to force a package version lower then 2.6 for the top 3 (package menu).

i appologize im a bit of a newbie to the coding game so how wud i manually install them ? and how would i force a package ?

---

### Post by waterboy0911 on 2011-07-20
> **khalidabuu said:**
> i appologize im a bit of a newbie to the coding game so how wud i manually install them ? and how would i force a package ?

here is a simple step..

1. go to system
2. go to administration
3. go to Synaptic Package Manager
4. on the main menu go to settings
6. on Ubuntu software tab tick all boxes and close 
5. click reload reload button
6. start searching and installing new apps using synaptic
6. go to your kitchen and have some beer to celebrate 

hope this helps!!

cheers

---

### Post by Jony35359595 on 2011-07-20
> **waterboy0911 said:**
> here is a simple step..

1. go to system
2. go to administration
3. go to Synaptic Package Manager
4. on the main menu go to settings
6. on Ubuntu software tab tick all boxes and close 
5. click reload reload button
6. start searching and installing new apps using synaptic
6. go to your kitchen and have some beer to celebrate 

hope this helps!!

cheers
in latest versions of Ubuntu you dont need synce to get your WM devices to work, so this threat died a year ago...

---

