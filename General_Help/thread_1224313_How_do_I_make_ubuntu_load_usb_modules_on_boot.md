---
title: "How do I make ubuntu load usb modules on boot?"
date: 2009-07-27
forum: General Help
---

### Post by Frogging101 on 2009-07-27
This is harder than the title makes it sound. Right now, I have ubuntu AND GRUB intalled on an external hard drive in its own ext3 10GB partition. When I turn on the computer with the external HDD attached, it will show me the grub menu. I select ubuntu from the menu, and press enter. The red gradient bar moves from side to side, but not accessing the hard drive. After a while, it gives up and drops me to a busybox prompt with an error about not being able to find the hard drive.

Now, I am able to fix this by typing the following commands (seperated by line):

modprobe usb-storage
modprobe ehci_hcd
modprobe sd_mod
modprobe scsi_mod
exec init

The system will now boot into ubuntu, and everything works fine. BUT... As you can imagine, having to type a string of commands every boot is an inconvenience that needs addressing.

And just to save time, I will say this: PLEASE do not answer with something like: "Well, you shouldn't use an external hard drive in the first place," or "I think you can live with having to type those commands." This is purely because I hear too many of these kinds of answers and the bottom line is, they don't answer the question.

Now, back to the problem...
As I said, typing the above commands will allow it to boot into ubuntu. I would like to find a way to make those commands run automatically before it tries to load ubuntu. You may suggest putting some lines into a file such as /etc/modules. But as I said before, it boots into busybox, and as far as I know doesn't access the drive until the commands above have been typed. This suggests that it won't recognize the drive until then. So when it boots into busybox and type 'ls', it doesn't show the files on my external hard drive, it shows a directory similar to the one on my drive, but missing some folders such as 'boot' and 'home'. In addition to this, if I create a file in this 'alternate filesystem', it will be gone after I reboot.

Haviing said all this, I will now ask the questions. If you need more information, or if something is unclear in any way, just tell me and I will gladly provide more information or clarification. Now, my questions are:

Where and what is this 'alternate filesystem' that I see when in busybox?
How can I make ubuntu load the modules before trying to start up?

---

### Post by Frogging101 on 2009-07-27
Bump. Any ideas?

---

### Post by wojox on 2009-07-27
So BIOS won't let you boot from usb first, huh?

---

### Post by Frogging101 on 2009-07-27
Well, GRUB is installed on the external hdd... and that works, and then i try to boot ubuntu... It's a long story, read the first post.

---

### Post by Frogging101 on 2009-07-27
Problem solved! For all of you who may see this on google or something:

I followed a guide that said how to build a new initrd.img, and have ubuntu automatically load the necessary drivers at startup. The guide can be found here: [http://stuporglue.org/initrd.php](http://stuporglue.org/initrd.php)

And if that goes down, can be very annoying especially if you think you have finally found the answer, then please just email me at [email]Brooks572@hotmail.com[/email], and I will send it to you.

---

