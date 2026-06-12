---
title: "Wired PS3 Controller in Ubuntu 10.10"
date: 2010-10-31
forum: General Help
---

### Post by AAndrew on 2010-10-31
I've been trying to configure my PS3 controller to work (wired) on Ubuntu 10.10 for the past hour.

I would like the controller to work with Mupen64Plus (N64 Emulator). My computer does't support bluetooth, so the connection has to be wired.

Anybody know how to get this to work?

---

### Post by AAndrew on 2010-10-31
Keeping the thread alive... Does anybody have a solution to this?

---

### Post by shade2dope on 2010-11-02
I really hope someone out there knows ! Ive been looking around too. If I find something I'll post info.

---

### Post by shade2dope on 2010-11-02
Well it seems that you can just change the input to the ps3 controller... I just this at first and it didnt work but know.... lol

---

### Post by shade2dope on 2010-11-02
Know time to figure out howto configure it on mupen64plus... I have the option just cant change them for some reason

---

### Post by Ocxic on 2010-11-02
nm

---

### Post by shade2dope on 2010-11-03
> **Ocxic said:**
> nm
lol ok ???

---

### Post by JellyBeanRacer on 2011-05-08
So there is no solution as of yet for this problem? I'm in the exact same boat.

I have been raiding Google trying to find an answer.

**EDIT:** found an answer for anyone with the following problem:
Mupen64 Plus recognizes you have a PS3 controller plugged in, but when you click to assign buttons, it immediately assigns a nameless axis to the button you were editing and then goes back to the previous menu.

Note: this fix makes the right joystick virtually useless.

(1) Choose a button you want to modify.
(2) While tapping the button on the PS3 controller repeatedly which you want to use, keep clicking in Mupen64 on the button you want to modify until the button input is registered before the nameless axis. This can take 15-20 tries or more.
(3) You should now have a button assigned (which will show as a number) and a nameless axis assigned to the input you chose.
(4) Now, while rotating the PS3's right joystick in circles, keep clicking on that input again until it registers the right joystick's axis instead of the nameless axis. You will see either U or Z, + or -.
(5) Repeat for each button you want to assign. Each button must have the PS3's right joystick assigned as its axis.
(6) Do not attempt to modify the left joystick's default inputs.

Yeah, that's a really ghetto, stupid way to fix this, but it works. For me, I assigned all the buttons to the left, down and right axis's of the right joystick so I can still use the up direction as Up C.

I guess this will work until my bluetooth dongle arrives. Apparently there are no issues like this with bluetooth.

---

