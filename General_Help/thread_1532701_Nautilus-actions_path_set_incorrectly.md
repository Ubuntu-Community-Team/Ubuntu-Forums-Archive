---
title: "Nautilus-actions path set incorrectly"
date: 2010-07-16
forum: General Help
---

### Post by Ralph L on 2010-07-16
I am installing lucid, have installed nautilus-actions, and am trying to install a "Search for file in the active folder" function into nautilus-actions..  I brought up Nautilus Actions Configuration under  System>Preferences and did the following:

 Under Action tab
   Checked Display item in selection context menu
   Unchecked Display item in location context menu
   Label:  Search For File In Active Folder
   Unchecked Display item in toolbar
   Tooltip:  Find files including path
   Icon:  gtk-find
   Action properties:  Checked enabled, unchecked Read_only
 Under Command tab
   Profile: Default profile
   Path:  gnome-search-tool
   Parameters:  --path=%M
 Under Folders tab
   /
 Under Conditions tab
   Filenames:  *
   Match case:  unchecked
   Mimetypes:  */*
   Appears if selection contains:  Only folders
   Unchcked Appears if selection has multiple files or folders
 Under Advanced Conditions tab
   Checked file.  
   Left all others unchecked.

My problem is that when I right click a folder and select "Search For File in Active Folder, it brings up the search tool, but the folder setting is always my home folder--not the active folder.  Of course I can change the folder to be searched, but the point was to search in the active folder.  I got this Search For File in Active Folder function from an Internet site that I don't remember.  However, I thought the --path=%M would get me the active folder.

Any help would be appreciated.

Ralph

---

### Post by Ralph L on 2010-07-19
The problem was that nautilus-actions 2.30.2 (distributed with lucid) has a long standing bug.  It is described in [https://bugzilla.gnome.org/show_bug.cgi?id=617058](https://bugzilla.gnome.org/show_bug.cgi?id=617058) , [http://ubuntuforums.org/showthread.php?p=8490250#post8490250](http://ubuntuforums.org/showthread.php?p=8490250#post8490250) , and [https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/570060](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/570060)

The solution is to install nautilus-actions 2.30.3 as described in [http://theubuntunews.blogspot.com/2010/07/nautilus-actions-2303-ubuntu.html](http://theubuntunews.blogspot.com/2010/07/nautilus-actions-2303-ubuntu.html)

The problem is almost solved.  The only problem is that the full path to the searched folder is not given--only the selected folder and its subfolders.  But I think I can live with this.

Hope this can be of use to somebody

Ralph

---

### Post by Scooby-2 on 2012-03-14
The link to the instructions to install the v2.30.3 above is broken, so I've added them here (at least they worked for me). Real shame that 10.04LTS installs broken software 2 years after it was first posted as a bug.

First, remove the installed version:
Open Synaptic Package Manager and enter "nautilus actions" in the search box. On my screen the top entry was for nautilus, the second for nautilus-actions 2.30.2-0ubuntu1. Right-click this and select "Mark for removal." (Don't select "Mark for complete removal" or you will lose any actions you have written and/or installed.) Click Apply.

Then install the new version:
Paste the following link into your browser or click the link:  
[https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid/+build/1787278/+files/nautilus-actions_2.30.3-1%7Elffl%7Elucid%7Eppa_i386.deb]("https://launchpad.net/%7Eferramroberto/+archive/linuxfreedomlucid/+build/1787278/+files/nautilus-actions_2.30.3-1%7Elffl%7Elucid%7Eppa_i386.deb")
This will hopefully download the file "nautilus-actions_2.30.3-1~lffl~lucid~ppa_i386.deb." Save it to your desktop (or wherever) and just double-click it when it's finished downloading. Ignore the message about the official version that's available through the Ubuntu channel.

Hope this helps someone.

---

### Post by Scooby-2 on 2012-03-14
Unfortunately version 2.30.3 has the exact same problem from which the conclusion is that the Nautilus Actions Configuration Tool is almost completely unusable in Ubuntu 10.04 LTS.

Shame. :(

---

