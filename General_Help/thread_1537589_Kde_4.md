---
title: "Kde 4"
date: 2010-07-23
forum: General Help
---

### Post by lorenzo.lewisjr on 2010-07-23
How can you install KDE 4 on Ubuntu

---

### Post by Yuri sss on 2010-07-23
[LIST=1]
[*]Open Synaptic (it's under Administration in the Gnome menu).
[*]In Synaptic, go to Settings -> Repositories.
[*]In the Software Sources window, change to the "Other Software" tab.
[*]Click on the "Add" button, then enter the following:
**ppa:kubuntu-ppa/ppa**
and click on "Add source".
[*]Click on the "Add" button, then enter the following:
**ppa:kubuntu-ppa/backports**
and click on "Add source".
[*]Close the Software Sources window.
[*]Click the "Reload" button in Synaptic, and wait until it's done updating.
[*]Enter **kde-full** in the search box.
[*]Right-click the package **kde-full** in the list and select "Mark for installation". Confirm the dialog that comes up by clicking on "Mark".
[*]Click on "Apply" in Synaptic, and again on "Apply" in the upcoming dialog, and it will start downloading and installing.
[/LIST]

Download and install will take a while. Click on the checkbox in the download dialog to see the individual download progress for the files.

---

### Post by watupgroupie on 2010-07-23
I assume Kubuntu isn't an option at this point :P

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) There you go :)

Edit: Oops didn't see Yuri sss's response.

---

### Post by Yuri sss on 2010-07-23
> **watupgroupie said:**
> I assume Kubuntu isn't an option at this point :P

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) There you go :)

Edit: Oops didn't see Yuri sss's response.
That article isn't too helpful for newbies...
Besides, if you just install right away without adding the Kubuntu repositories first, you'll get a quite outdated version of Kde4.

---

