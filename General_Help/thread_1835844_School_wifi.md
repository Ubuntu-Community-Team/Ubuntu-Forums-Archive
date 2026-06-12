---
title: "School wifi"
date: 2011-08-30
forum: General Help
---

### Post by buttersauce on 2011-08-30
So at the new school i go to they have a Wifi.  The wifi is listed as unprotected but on windows when you open a browser there will be a sign in page where you use a user name and password.  Ubuntu will not let me go to that page even if i am connected to the internet.

anyone know what to do?



SOLVED - thanks guys... i wrote down the proxy from windows and then retyped it on ubuntu... thanks for all your help.  Now i have a new problem... sigh...
  
[http://ubuntuforums.org/showthread.php?t=1837067](http://ubuntuforums.org/showthread.php?t=1837067)

---

### Post by sbraz on 2011-08-30
ask a professor for access using social engineering?

edit: sorry i didn't read all of your question. :(

---

### Post by 3xp10r3r|X13 on 2011-08-30
it seems as your school is using a proxy server, which most do. therefore, you've got to set the browser to the proxy server.

---

### Post by ofnuts on 2011-08-30
> **buttersauce said:**
> So at the new school i go to they have a Wifi.  The wifi is listed as unprotected but on windows when you open a browser there will be a sign in page where you use a user name and password.  Ubuntu will not let me go to that page even if i am connected to the internet.

anyone know what to do?Connected to the Internet or to the wifi network? If connected to the Wifi, what is the answer to 'ifconfig wlan0' once you are connected? An what are the contents of /etc/resolv.conf?

---

### Post by holycow131415 on 2011-08-30
I was at a hotel once where this happened, on a different linux OS. What i did was write down the url of the login page that i saw while in windows and entered it into firefox while in linux. it seemed like the login page was expecting IE, and no other browser.

Oh, and you should bookmark the login page (if this works)

---

### Post by pAsM on 2011-08-30
Its worth asking, but do you have your machine setup to dynamically obtain an IP with DHCP vs a static?

---

### Post by buttersauce on 2011-08-31
> **holycow131415 said:**
> I was at a hotel once where this happened, on a different linux OS. What i did was write down the url of the login page that i saw while in windows and entered it into firefox while in linux. it seemed like the login page was expecting IE, and no other browser.

Oh, and you should bookmark the login page (if this works)

I will try this tomorrow... Thanks.

---

### Post by buttersauce on 2011-08-31
> **sbraz said:**
> ask a professor for access using social engineering?

edit: sorry i didn't read all of your question. :(

I'm sorry i should have specified they give you the user name and password.  It is an open network for students and we are allowed to be using it.  I just cant get the screen to show up when i open my browser.

---

### Post by buttersauce on 2011-08-31
> **3xp10r3r|X13 said:**
> it seems as your school is using a proxy server, which most do. therefore, you've got to set the browser to the proxy server.

Is this basically what the last guy said?  going to it on windows, writing it down, then entering it on ubuntu?  if not can you explain further?  I am a total newbie to ubuntu.

---

### Post by ofnuts on 2011-08-31
My question(s) (23 hours ago) still hold ... you haven't yet ascertained that you are correctly connected.

---

