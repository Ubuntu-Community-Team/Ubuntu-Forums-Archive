---
title: "Midnight Commander and VIM"
date: 2011-01-20
forum: General Help
---

### Post by frrobert on 2011-01-20
I am using Ubuntu 10.04

I configured MC to use an external editor.

I also checked 

sudo update-alternatives --config editor  and VIM is selected.

When I select to view a file vim fires up, when I select to edit a file nano starts up.

Is there another setting I need to set so VIM fires when I select edit in MC?

---

### Post by frrobert on 2011-01-20
I just figured it out for some reason in Ubuntu 10.04 there are 3 steps

1.  Configure  MC to use an external editor

2.  sudo update-alternatives --config editor and select VIM

3.  Edit ~/.bashrc  to include

EDITOR=/usr/bin/vim
export EDITOR=/usr/bin/vim

---

