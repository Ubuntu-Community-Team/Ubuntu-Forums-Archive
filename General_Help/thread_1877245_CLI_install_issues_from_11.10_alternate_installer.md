---
title: "CLI install issues from 11.10 alternate installer"
date: 2011-11-07
forum: General Help
---

### Post by halitus87 on 2011-11-07
Hi,

I have installed a CLI system from an alternate installer iso (on a vm at the moment). I did this by using file=/cdrom/preseed/cli.seed in the boot options.(by the way I cant use the server version due to some raid issues)


This seams to install fine but when it boots it comes up with a "_" prompt only that i cant do anything with. I can alt-f1 and get to a shell. I thought that I could  change a line in /etc/default/grub to GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”.

However I cant install vim. I use apt-get install vim. But it says the package is not available but is referred to by another package. I cant install anything it seams. 

Any ideas? have I installed the cli version correctly?

thanks

Halitus

---

### Post by halitus87 on 2011-11-26
I have abandoned this and gone back to the server install. 

I feel that this is not unexpected behavior. I just don't understand how to install a CLI system.

oh well...

---

### Post by oldtimer7777 on 2011-11-26
You can use a pre-installed virtualized vdi file ... just download it and drop it in your VMWare or Virtualbox.

> **halitus87 said:**
> I have abandoned this and gone back to the server install. 

I feel that this is not unexpected behavior. I just don't understand how to install a CLI system.

oh well...

---

### Post by gmargo on 2011-11-27
> **halitus87 said:**
> Hi,

I have installed a CLI system from an alternate installer iso (on a vm at the moment). I did this by using file=/cdrom/preseed/cli.seed in the boot options.
...

Any ideas? have I installed the cli version correctly?


In the alternate installer, the F4 key brings up the "Modes" menu, one of which is "Install a command-line system". That's what I normally use.  Where did you get the "file=..." info?

---

