---
title: "help with command line password"
date: 2010-06-13
forum: General Help
---

### Post by lifesstudent on 2010-06-13
hello, I'm new to ubuntu.  anyway, I just installed ubuntu 10.04 and I was installing some programs.  later I was trying to use the sudo apt-get for esword and when it asked for my password, I was unable to type it.  it acts like I'm not typing anything.

I'm not sure if it is something I'm doing or if it is a bug. 

thank you for all who reads this.

---

### Post by efflandt on 2010-06-13
Note that there is no feedback for passwords typed for sudo, so nobody looking over your shoulder can tell how many characters your password has.

So you have to type it blind (make sure Caps Lock is off).  If you know you typed a wrong character you can use backspace, or Ctrl+U clears it entirely to start typing it from the beginning.

---

### Post by dim3000 on 2010-06-13
Also, try using Synaptic from System > Administration, you may find it easier than command-line.

---

### Post by dapperdanny77 on 2010-06-13
sudo isn't echoing your input with "****" or similar
just type your password and hit enter

if you type a wrong password - sudo complains about

---

### Post by lifesstudent on 2010-06-13
thank you all for your help! I finally understand and now have what I needed.

thank you again!

---

