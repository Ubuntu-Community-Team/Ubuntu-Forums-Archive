---
title: "Is there a screen capture command?"
date: 2011-06-15
forum: General Help
---

### Post by conradin on 2011-06-15
Hi all, 
I am writing an expect script and I want to send the command for the print-screen function. So, what is the command? Alternatively, is there some terminal application which may be well suited to take screen-shots via commands from the terminal or automation scripts?

---

### Post by inameiname on 2011-06-15
These are two aliases I have in my ~/.bashrc. One may work for you:

import -frame -strip -quality 75 "$HOME/$(date +%s).png"

and:

IMAGE="$HOME/Pictures/capture-`date +%Y%m%d%H%M%S`.png"; import -frame $IMAGE; echo "Image saved as $IMAGE

---

### Post by kerry_s on 2011-06-15
in a terminal type-> gnome-screenshot --help

---

