---
title: "Cannot Execute Binary FIle"
date: 2011-04-11
forum: General Help
---

### Post by jeffrich4 on 2011-04-11
I'm having issues with the error 'bash: executbalename: cannot execute binary file' in a few different areas. I'm running Ubuntu-OMAP on a BeagleBoard-xM and I'm currently trying to set up the DSP.

It first occurred when setting up the TI DSP binaries, there is an installer for the binaries with instruction to chmod +x to make it executable and then run it with ./, however it gives me the error.

In another instance, I was setting up CodeSourcery. I got it installed to $HOME/CodeSourcery and added the bin folder to PATH. Then when I go to verify with 'arm-none-linux-gnueabi-g++ -v' it gives the 'cannot execute binary file' again.

I have ran executable programs on it before so I'm not sure what the issue is here, any help would be appreciated!

---

