---
title: "Warning: Latest Karmic update kernel 2.6.31-21 may cause severe video card lock-up"
date: 2010-04-29
forum: General Help
---

### Post by DawieS on 2010-04-29
(Post to assist others with a similar problem.)

When the Update Manager ran this morning in Karmic, I was presented with the 'reboot now' option to complete the installation of a new kernel. Upon reboot, I noticed that my screen (Samsung SyncMaster 226BW) flickered beween 'Analogue' and 'Digital' for a while and then switched itself off, as if it does not detect any signal.

The same happened about 2 weeks ago after a Lucid beta2 update (I also have Lucid installed on an external drive). At the time I was able to reboot after disconnecting/reconnecting the power supply, and selecting the working Karmic installation in the BIOS. I then uncommented the line '#GRUB_TERMINAL=console' in the file '/etc/default/grub', after which Lucid booted up perfectly.

This time, I was not so lucky. I had to disconnect cables, open the box and unplug the video card from the motherboard before I was able to successfully boot again, and enter the BIOS. I uncommented the same line in Karmic, this time booted from Lucid. Ater a reboot the Grub menu then appeared and worked, however the cursor line kept on blinking, as if something is bothering Grub, even after a few 'sudo update-grub' and reboots.

I then uninstalled/reinstalled Grub as per section 12 of [_**this**_]("http://ubuntuforums.org/showthread.php?t=1195275") tutorial, after which Grub worked normally on reboots, as if there never was anything wrong. I also noticed that the line I uncommented, is commented again after reinstalling Grub. I cannot explain what actually went wrong, or was changed, to cause the lock-up.

The new Karmic kernel is very responsive, even under full loads, and is a definite improvement over previous kernels. It also seems as if Xorg uses much less %CPU.

Motherboard: Gigabyte S-Series GA-MA69G-S3H
Video Card: XFS GeForce 8400 GS

I know that I am due for an upgrade on hardware, but if you have grown-up kids, somehow they always end up with the cream of the crop, and you with the leftovers.
:smile::razz::smile:

---

