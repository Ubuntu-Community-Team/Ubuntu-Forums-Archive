---
title: "cannot get display or bios after resizing partition during natty narwal install"
date: 2011-03-08
forum: General Help
---

### Post by axarms on 2011-03-08
hi guys
       i was installing ubuntu 11.04 natty narwal daily build alongside windows 7 and ubuntu 10.10, and was resizing partition when computer was taking too long to resize, i then restarted computer, my computer appears to be working, but i get no display on my monitor, even though it is powered on.
   i would appreciate any help in getting my bios to appear, or restoring my computer to normal.
    thanking you in advance for any help.

---

### Post by Mark Phelps on 2011-03-08
Getting your PC back to normal is a BIG task -- one made even harder by the lack of details in your post.

If you shutdown your PC while it was resizing a partition (which is how it reads), then your hard drive is likely trashed -- and any OS is likely NOT to boot anymore due to that.

However, none of that will affect the BIOS, so you should be able to see that.  Next time you boot, hold down the Del key to see if that forces you into BIOS edit mode.  Then, go into the BIOS and see if you have an option to show the BIOS details when booting.  IF that is turned off, it's likely you won't see anything on screen until you boot into an actual OS desktop.

---

### Post by axarms on 2011-03-09
to mark phelps
              sorry about the lack of details.
i tried the delete key when booting i hear one beep but still no display. i have also taken out the cmos battery for over 2 hours then replaced it still no display on monitor although it is powered up.
   would appreciate any more help.
                                  thank you

---

### Post by srs5694 on 2011-03-09
Try disconnecting the hard disk from the motherboard and see if you can get to a BIOS screen. If so, the BIOS is trying to read something from the partition table and is getting confused by damage. You might be able to correct it by plugging the drive in via a USB adapter, or risking a "hot plug" of the USB device (I'd try this only with SATA drives, and then only with some trepidation).

---

### Post by axarms on 2011-03-10
to srs5694
         i have tried removing hard drives from motherboard, still no display although monitor still powers up then goes into standby (flashiing orange light) the same as before.
  thank you for your input, if there is anything else i could try,i would welcome any replies.

---

### Post by srs5694 on 2011-03-10
At this point, my best guess is that the motherboard, CPU, or memory is fried. Probably it died during the resize operation, which caused it to fail and is now making the system unbootable. If you happen to have spare RAM sitting around, you could try swapping it out; or if you've got two memory sticks in the computer, you could use one and try with just half the memory. (Read the motherboard manual, though; some boards have requirements about which slot to use if you use just one memory stick.)

Best of luck; this type of debugging is particularly hard, especially if you don't have a shelf full of spare parts to use for replacements.

---

### Post by axarms on 2011-03-11
to all, i took my computer to be repaired windows 7 was reinstalled.
i never saw any post when booting up, the computer went to windows password, i inserted my password windows booted up i then updated
and was told to restart which i did, computer restarted, i could hear windows in the background, but NO DISPLAY on monitor. i tied another monitor same again windows working in the background, but again NO DISPLAY on monitor. i have left the computer running for hours still no change.
                      thank you for any suggestions

---

### Post by axarms on 2011-03-11
SOLVED thanks to google and the internet.
 the solution is as follows
  UNPLUG YOUR COMPUTER POWER PLUG
  PUSH AND HOLD YOUR COMPUTER POWER BUTTON FOR BETWEEN 1 TO 2 MINUTES
  PUT YOUR COMPUTER BACK ON.
  and strangely enough my computer display came back on.
  the only thing is when i restart my system the display disappears again. so i tried the same trick again, and i got my display back yet again. 
    SO IS THERE ANYWAY TO STOP THIS HAPPENING? AGAIN
i do not want to repeat the trick everytime i restart my computer.
   THANKS for any further information or input from fellow forum members.

---

### Post by srs5694 on 2011-03-11
Given the new information, I'll update my former best guess: The video circuitry on your motherboard is damaged. If so, adding a separate video card should fix the problem.

---

### Post by axarms on 2011-03-16
SOLVED  i unplugged my dvi cable from my monitor, and then attached my vga cable to my monitor.
   LO and BEHOLD, i got my display, post and bios back to normal.
  THANKS to everybody for their help and hints.

---

