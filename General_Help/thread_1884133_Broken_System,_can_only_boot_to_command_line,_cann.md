---
title: "Broken System, can only boot to command line, cannot post logs from that system"
date: 2011-11-20
forum: General Help
---

### Post by Amurko on 2011-11-20
I have a system that was casually turned off by an uninformed person while it was upgrading from 11.04 to 11.10.

Now it won't boot up.

I booted using the Live CD, selected the Rescue Broken System option.

In the boot options, I delete "VGA=788" and I could boot to a command line system.  (If I don't delete that part, it would boot to a blank screen.)

It finally got to the point where I could select a drive to boot from.

I selected /dev/sda1.

It connected to the network and gave me a command prompt.

I issued the command "sudo dpkg --configure -a"

**It tried to continue the upgrade for several minutes until it gave a bunch of errors.**

There were LOTS of errors, so many that they didn't fit on one screen.

Then it terminated saying "Processing was halted because there were too many errors."

I tried "sudo apt-get install -f" and I also got "Processing was halted because there were too many errors." after it tried fixing some errors.

I tried going back to "sudo dpkg --configure -a" and it still gave a LONG list errors.

I need help at this point.

But before you ask me to post any logs or sorts, please tell me how I can extract logs from a computer without any working graphical interface and no working cut-and-paste functionality.

Please walk me through how to mount a USB drive or burn a CD from the command line and how to save the output of every command to a file on the USB drive.

---

### Post by jerrrys on 2011-11-22
been there, and **sudo apt-get update** save my bacon

---

