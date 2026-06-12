---
title: "gvim file:open dialog unusably slow"
date: 2011-08-28
forum: General Help
---

### Post by stair314 on 2011-08-28
Just installed Ubuntu 11.04 on a new machine a few days ago.
Right now I'm trying to use gvim on this machine for the first time.
I installed it with
sudo apt-get install vim-gnome

When I click on the open file button, I get an open file dialog. It loads quickly with an ls of my home directory, but when I select a subdirectory, it takes literally several minutes for the file dialog to ls that subdirectory. This happens again for each nested subdirectory I need to open.

This shouldn't be a filesystem problem: I can ls the same directories from the terminal in a split second, and they are not any kind of exotic networked directory or anything. They are just directories on a good old-fashioned magnetic hard drive in the same PC I'm sitting at.

Also, gvim hasn't crashed. If I click the "cancel" button on the file open dialog, it responds to that.

Any ideas what could be causing this?

Thanks in advance

---

### Post by fogbrain99 on 2011-09-04
Open a terminal window and enter

export UBUNTU_MENUPROXY=0
gvim

every time you want to run gvim.  This turns off the new magic Unity menus and fixes the file open problem for some unknowable reason.

---

### Post by stair314 on 2011-09-11
That works, thanks.

---

