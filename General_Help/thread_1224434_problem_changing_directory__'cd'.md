---
title: "problem changing directory  'cd'"
date: 2009-07-27
forum: General Help
---

### Post by drdob on 2009-07-27
dear all i have a problem changing directory i have fallowed directions in this site and in the books, but on the computer it does not work :( I am try to change directory to desktop but it (computer) will not co-operate :confused: any ideas?? thanks Dr Dob

---

### Post by TeoBigusGeekus on 2009-07-27
What is the exact command you're using?
It should be
```
cd ~/Desktop
```

---

### Post by decoherence on 2009-07-27
> **drdob said:**
> dear all i have a problem changing directory i have fallowed directions in this site and in the books, but on the computer it does not work :( I am try to change directory to desktop but it (computer) will not co-operate :confused: any ideas?? thanks Dr Dob

Hi there,

Specifically what instructions are you following?

When you say it doesn't co-operate, how does it fail?

To change directory, type

```
cd *path/to/directory*
```

you can confirm it put you where you wanted with the command 

```
pwd
```

which stands for "print working directory"

---

### Post by DaithiF on 2009-07-27
you are aware that paths are case sensitive?  I noticed that you wrote 'desktop' in your question rather than Desktop.

```
cd ~/desktop   
```
will not work, but 
```
cd ~/Desktop 
```
will

---

### Post by t4thfavor on 2009-07-27
Typical Windows convert mistake. All Linuxes/Unixes/Non Windowses are Case SEnSative. So ~/desktop != ~/Desktop != ~/DeSkTop.

No worries, you will begin to like it. I know I have.

---

### Post by drdob on 2009-07-27
thank you all for your quick answer . i am using "cd Desktop" but tried cd ~/Desktop and it worked thank you i will get the hing of it one day .. TeoBigusGeekus and DaithiF get the lolly pop

---

### Post by Monotoko on 2009-07-27
The reason 
```
cd Desktop
```

didnt work was because linux follows a certain system, everything begins at root (much the same in Windows, everything begins at C:\)

so to get to your desktop, lets say the user logged in is "chipmonk", you would do this to get to your desktop

```
cd /home/chipmonk/Desktop
```

-----

The ~ in
```
cd ~/Desktop
```

represents your home directry, so /home/chipmonk is the same as ~

:)

(Much the same as C:\Documents And Settings\chipmonk is your home folder on Windows)

---

### Post by drdob on 2009-07-28
Monotoko thank you, now i get :o just think every day i'm getting better and better :popcorn: Dr Dob

---

