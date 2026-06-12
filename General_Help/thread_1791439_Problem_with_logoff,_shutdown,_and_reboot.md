---
title: "Problem with logoff, shutdown, and reboot"
date: 2011-06-26
forum: General Help
---

### Post by ultimatebuster on 2011-06-26
Everytime I log off, I get booted to console and get this error:

> Jun 26 20:05:51 ulti-laptop kernel: [153829.445165] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:05:51 ulti-laptop kernel: [153829.445256] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996
Jun 26 20:05:56 ulti-laptop kernel: [153834.465200] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:05:56 ulti-laptop kernel: [153834.465283] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996
Jun 26 20:05:56 ulti-laptop kernel: [153834.465372] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C04A (len 871, WS 0, PS 0) @ 0xC0A7
Jun 26 20:06:01 ulti-laptop kernel: [153839.684811] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:06:01 ulti-laptop kernel: [153839.684892] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CD06 (len 72, WS 0, PS 0) @ 0xCD35
Jun 26 20:06:06 ulti-laptop kernel: [153844.684807] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:06:06 ulti-laptop kernel: [153844.687110] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996
Jun 26 20:06:11 ulti-laptop kernel: [153849.884495] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:06:11 ulti-laptop kernel: [153849.886863] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996
Jun 26 20:06:16 ulti-laptop kernel: [153855.084141] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:06:16 ulti-laptop kernel: [153855.086465] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996
Jun 26 20:06:21 ulti-laptop kernel: [153860.283794] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:06:21 ulti-laptop kernel: [153860.337419] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996
Jun 26 20:06:27 ulti-laptop kernel: [153865.583235] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 20:06:27 ulti-laptop kernel: [153865.585736] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C97A (len 62, WS 0, PS 0) @ 0xC996

I'm on an IdeaPad Y460 and I have an ATI HD 5650 powered off using this method: [http://ubuntuforums.org/showthread.php?p=10955831#post10955831](http://ubuntuforums.org/showthread.php?p=10955831#post10955831)

Any idea why?

Also I can't shutdown and reboot without pressing the powerbutton, but idk where the log file is. If someone tell me where they are I could post it.

Also, I don't relog into the first GUI (CTRL + ALT + F7), rather I boot into the second one after logging in (CTRL + ALT + F8). I don't know if that's a feature or the same bug.

---

