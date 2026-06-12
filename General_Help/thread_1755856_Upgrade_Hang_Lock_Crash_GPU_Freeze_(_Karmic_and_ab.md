---
title: "Upgrade Hang Lock Crash GPU Freeze ( Karmic and above ) Intel 915 chipset"
date: 2011-05-11
forum: General Help
---

### Post by harrismh777 on 2011-05-11
LaunchPad Bug # 451518

The purpose of this paper is to document a possible work-around for bug 451518, and others related to a freeze of the GPU graphics processor related to the Intel 910GML / 915GM / 915GMS / 915GV / and 910GL Express Chipsets and Intel's DVMT Dynamic Video Memory Technology  and the i915 driver.

The surface condition looks and feels like a total system crash--- the keyboard is dead (unresponsive in all modes, no numlock light, no caps light), the mouse is dead, the screen is blank the the power light blinking (video off) and the system appears completely lifeless. 

Actually, the GPU (onboard Graphics Processing Unit) has frozen ( freeze-up, freeze, locked, crashed) and the system is up and running otherwise (a hallmark of linux generally!). The machine will respond to a network ping, and if configured correctly, can be accessed through ssh secure shell for remote inspection, graphics restart (sometimes does not work), or reboot. In other words, the system has not crashed (is not in a crashed state); however, the GPU is dead, and the user is unable to access the system from the keyboard, mouse, and display.

Most folks notice this problem after upgrading to Karmic (or above), with the graphics options enabled, compiz.real running, and some other graphics intensive app running particularly but not limited to the gnome screen saver (screensaver). The following appears in my logs repeatedly before the GPU crash (hang, lock, freeze):    (logging appears to be in a loop, every two minutes)

kernel: [17760.452041] i915/0  D c081b5c0  0 274  2 0x00000000
kernel: Call Trace:
kernel: [<c0574476>] __mutex_lock_slowpath+0xc6/0x130
kernel: [<c0574390>] mutex_lock+0x20/0x40
kernel: [<f814bb3a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
kernel: [<c0157a2e>] run_workqueue+0x6e/0x140
kernel: [<f814bb10>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
kernel: [<c0157b88>] worker_thread+0x88/0xe0
kernel: [<c015c1d0>] ? autoremove_wake_function+0x0/0x40
kernel: [<c0157b00>] ? worker_thread+0x0/0xe0
kernel: [<c015bedc>] kthread+0x7c/0x90
kernel: [<c015be60>] ? kthread+0x0/0x90
kernel: [<c0104047>] kernel_thread_helper+0x7/0x10


This problem is reported in launchpad bug # 451518 (and others) and appears to be related to the 915GV Intel integrated video chipset ( also 900 945 ? ) and the i915 driver ( and or mesa ); upgrade seems to trigger the problem. Disabling the gnome screen saver has been a work-around; also shutting down compiz.real.  

This problem is related to Intel's DVMT Dynamic Video Memory Technology, and the i915 driver, and or mesa. The bug # 451518 is still open and unresolved; however, making a DVMT setting change in BIOS has proven to be a work-around in some situations (my system GPU has not crashed / hung since disabling DVMT memory in priority to fixed memory, in BIOS).

Default systems have shipped with 512M system memory, or lower, default to 8M preallocated video memory, 0M fixed memory, and 120M DVMT memory. The i915 driver and or mesa are not handling DVMT correctly. Changing the BIOS setting to:

  8M preallocated, 120M fixed,  0M DVMT

... has proven to be a successful work-around for bug # 451518.  In some BIOS this change amounts to picking the correct table entry for all three values together. Multiple configution options are permitted. Setting DVMT to zero (0) effectively places a fixed amount (in this case 128M) of video memory at the top available all the time. On systems with 512 or less of system memory a setting of :

  8M,  64M,  56M     ... will also work.

On systems with more than 512M of system memory can afford to allocate the full 128M to fixed memory... my machine has 2gig... no problem,.

The Intel DVMT 3.0 White Paper (pdf) can be found here, helpful for explanation and BIOS configuration options:

[http://download.intel.com/design/chipsets/applnots/30262305.pdf](http://download.intel.com/design/chipsets/applnots/30262305.pdf)


Cheers,

m harris

---

