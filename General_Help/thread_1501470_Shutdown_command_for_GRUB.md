---
title: "Shutdown command for GRUB?"
date: 2010-06-04
forum: General Help
---

### Post by chemicalrubber on 2010-06-04
At the GRUB menu, what is the command to shut down? Typing "halt" in the command line doesn't work and only hangs the computer on the command line screen. Heard that "init 0" works?

---

### Post by oldfred on 2010-06-04
It must depend on computer I used this with grub2 and had the same with grub legacy (in its format). But I have seen others where it has not worked.

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

---

