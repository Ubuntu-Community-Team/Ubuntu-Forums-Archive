---
title: "Need help with WINE on Linux!!!"
date: 2010-07-29
forum: General Help
---

### Post by nkdnaskdn on 2010-07-29
I want to play full tilt poker and wow and stuff but i downloaded wine and full tilt. And when i tre to run the set up i get that error message for the archive, X( Please help!!!

---

### Post by davidmohammed on 2010-07-29
we need more help from you to help you...

what is the error message?  Can you describe step-by-step what you are doing, how you did it and what you are seeing on the screen.  Thanks.

---

### Post by nkdnaskdn on 2010-07-29
Well i went to the site and downloaded wine.. There was an ubuntu package but i didnt click it... then i Downloaded Full tilt, and tried to run it. The error message is.
End-of-Central-Directory signature not found.

---

### Post by 3rdalbum on 2010-07-29
[http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

---

### Post by nkdnaskdn on 2010-07-29
???

---

### Post by davidmohammed on 2010-07-29
what you you mean "went to the site and downloaded wine"? 

You should ALWAYS install software from the software centre or synaptic manager.

The package you want is called wine 1.2.

Google revealed this video on how to [install]("http://www.youtube.com/watch?v=xDlBUK_NcSI") Full Tilt.  Hopefully it will work for you.

---

### Post by nkdnaskdn on 2010-07-29
Umm well, im at winehq.org. And i went to the ubuntu package, it goes through some steps but... when i have to reload the package info, i get an error there as well >.<

---

### Post by davidmohammed on 2010-07-29
oops - seems like you've got your PC package manager in a bit of a state...

What is the error message (the full message what you are seeing on the screen)?

---

### Post by nkdnaskdn on 2010-07-29
Well it appears i didnt have wine officially installed. WHich i do now. But that error i dont see.. So i went to that other guys comment and went through those steps, at the very very end when im in Terminal and i drag my full tilt set up in the box it says premission denied. You know anything about that?

---

### Post by davidmohammed on 2010-07-29
I presume you have downloaded some sort of .exe file?

when you are in the terminal type

ls

it should list the full name of the exe file.  If you have downloaded the file into another directory then type

cd <directory>
e.g. cd Downloads

then type

chmod +x <exe file name>

e.g.

chmod +x fulltiltexe.exe

finally install via

wine <exe file name>

i.e.

wine fulltiltexe.exe

You may have to do other stuff to get fulltilt to work.  Does the video show you what stuff you have to do?

---

### Post by nkdnaskdn on 2010-07-29
Thats a little confusing for me... Im in terminal and stuff but..what confuses me is the "lg" where do i type that in the terminal box? like after i do wine or something?>

---

### Post by davidmohammed on 2010-07-29
"ig" - I'm confused - does the video ask you to type that?

---

### Post by nkdnaskdn on 2010-07-29
There is no vidfeo its just steps, and you said to type LG to do something im so confused >.<.... Is it possible to use team viewer with you? as like an easier way to do this?

---

### Post by Joe of loath on 2010-07-29
> **nkdnaskdn said:**
> There is no vidfeo its just steps, and you said to type LG to do something im so confused >.<.... Is it possible to use team viewer with you? as like an easier way to do this?

What's so confusing about those steps? You can copy and paste most of them...

---

### Post by nkdnaskdn on 2010-07-29
They arent. Just i followed evreything then it just said permission denied and now idk what to do.

---

### Post by nkdnaskdn on 2010-07-29
OMG I GOT IT! Dumbass me was hitting enter after i typed "wine" DUH! Thanks!!!!

---

### Post by davidmohammed on 2010-07-29
Team Viewer isnt software that I have installed - nor do I intend to install it!

If you have a IP address I can connect to you via "internet - Remote Desktop Viewer" then happy to help - if you are behind a firewall or a router you'll need obviously to configure your firewall/router appropriately.  Just PM (private message) me the IP address.

---

