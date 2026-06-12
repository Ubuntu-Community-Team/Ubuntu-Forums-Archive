---
title: "Problem with login as normal user."
date: 2012-07-13
forum: General Help
---

### Post by polloconpatatas on 2012-07-13
I´ve problem with my user login.

When ubuntu starts, at user & password login menu, y check my pass to log in but all ubunto does is a beep sound, black screen, and returns to start menu asking login and pass again.

No errors, "wrong pass" or something else.

It fails only with my user, if i try to log as guest everything is ok and it stats with no problem.

Any idea aboout it? How can i solve this problem?

Thank you.

---

### Post by steeldriver on 2012-07-13
It sounds like there is something preventing your xsession from starting properly

Hit Ctrl-Alt-F1 and try to log in at the virtual terminal - if that works type

```
ls -ld ~
```and

```
ls -al ~/.*authority
```Post back with the results

---

### Post by Rebelli0us on 2012-07-13
> **polloconpatatas said:**
> I´ve problem with my user login.

When ubuntu starts, at user & password login menu, y check my pass to log in but all ubunto does is a beep sound, black screen, and returns to start menu asking login and pass again.

No errors, "wrong pass" or something else.

It fails only with my user, if i try to log as guest everything is ok and it stats with no problem.

Any idea aboout it? How can i solve this problem?

Thank you.


Does the account have a password? If no PW has been set, all you have to do at login is press Enter.

---

### Post by polloconpatatas on 2012-07-13
Yes, this account has password :D, this is not the problem

---

### Post by polloconpatatas on 2012-07-13
> **steeldriver said:**
> It sounds like there is something preventing your xsession from starting properly

Hit Ctrl-Alt-F1 and try to log in at the virtual terminal - if that works type

```
ls -ld ~
```and

[COLOR=Blue]drwxr-xr-x 23 ber ber 1144 jul 13 18:28 /home/ber[/COLOR]

```
ls -al ~/.*authority
```Post back with the results

[COLOR=Blue]-rw------- 1 ber  ber  2338 jul 13 00:53 /home/ber/.ICEauthority
-rw------- 1 root root  104 jul 13 00:53 /home/ber/.Xauthority[/COLOR]

[COLOR=Blue][/COLOR]

---

### Post by steeldriver on 2012-07-13
OK so your ~/.Xauthority file got owned by root - if you have sudo permissions you can just delete it:

```
sudo rm ~/.Xauthority
```Then press Ctrl-Alt-F7 to get back to the GUI display manager and try again

---

### Post by polloconpatatas on 2012-07-13
Great! it worked.

Thank you so much!

---

