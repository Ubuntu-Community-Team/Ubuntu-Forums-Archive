---
title: "Ctrl + alt + Delete equivalent?"
date: 2011-04-26
forum: General Help
---

### Post by roadkillguy on 2011-04-26
I've been working on a c++ project for a couple months now.  Unfortunately, every time I mess with input handling code, I end up starting SDL_GrabInput and am never able to handle the input that would normally close the application.

Is there some alternative to shutting down the machine just because some indie app has my input and wont let go?

Thanks a bunch.

---

### Post by zealibib slaughter on 2011-04-26
Ctrl+alt+backspace if enabled will restart the x server which will kill the app and bring you back to the login prompt. See this [link]("http://www.ubuntugeek.com/enable-ctrl-alt-backspace-in-ubuntukubuntu-10-04lucid-lynx.html") to find out how to enable it. 
 
and
ctrl+alt+F2 puts you to a terminal login.  Login and run the following.
killall name_of_app
this will kill the app you specify

---

### Post by MegaLoler on 2011-04-26
I am not sure if this is outside of the input that is frozen by that program or not, but if you can bring up the run dialog (alt-f2) and enter xkill you can click on the program's window when the skull and cross bones cursor appears.

---

### Post by roadkillguy on 2011-04-26
ctrl+alt+backspace seems to kill all applications..

ctrl+alt+f2 brings me to a terminal alright, but is there any way to get back into the desktop?

I only wish to break input, not kill everything.. maybe that's impossible.

Edit: alt+f2 is within the frozen input

---

### Post by coffeecat on 2011-04-26
As an alternative to enabling ctrl-alt-backspace to kill the xserver, you can use the key combination alt-Printscrn-K.

If the system is really locked up and you need to shutdown or reboot gracefully, you need a magic key combination. See here:

[http://en.wikipedia.org/wiki/Magic_key](http://en.wikipedia.org/wiki/Magic_key)

In fact, as you can see, alt-Print-K is one of the magic key combos.

---

### Post by zealibib slaughter on 2011-04-26
> **roadkillguy said:**
> ctrl+alt+backspace seems to kill all applications..
 
ctrl+alt+f2 brings me to a terminal alright, but is there any way to get back into the desktop?
 
I only wish to break input, not kill everything.. maybe that's impossible.
 
ctrl+alt+f7 or f8 sometimes brings you back to gui.  You have 6 text terminals f1-f6 and 6 gui terminals f7-f12.  it is usually the first or second by default for x sessions.

---

### Post by coffeecat on 2011-04-26
> **roadkillguy said:**
> I only wish to break input, not kill everything.. maybe that's impossible.

Not impossible. Go to a virtual terminal with ctrl-alt-F1 or ctrl-alt-F2 and login. Run "top" to find the PID of the stuck process. Then 'sudo kill <PID>' to kill just that process.

**EDIT**: zealibib slaughter's use of killall in post #2 should have the same effect, although you *might* need to use sudo.

---

### Post by roadkillguy on 2011-04-26
F7 is a simple flashing cursor and F8 got me back to the GUI! Unfortunately, my input was still grabbed, so I used ps -d && killall to kill the application.  Thus, I killed the app without rebooting.

Edit::Ahh didn't see the edit in post 2..

Thanks!

---

### Post by trollger on 2011-04-26
Once you press ctrl+alt+f2 you have taken your self to the second terminal (I like to go to the 4th). to bring yourself back to your desktop first login and then press ctrl+alt+f7 wich is where your xserver/desktop is running also feel free to see whats running on the other 'screens' by pressing ctrl+alt+f1-7.

While in the console you can manage whats running on your computer by pressing 

```
 ps -A  
```to get a list of all running programms. If the list is to long to fit on the screen (and it will be) trype in 

```
 ps -A | more 
```to scroll though them, when you come to the procces you want to kill press q to stop the more program and then type kill (you may need to be sudo depending on the procces) then the PID procces id which is the number on the left about 5 digits long, Hit enter and if there is no error you can assume that that procces has been stopped. To launch a new program just type the program's name if there is a space in the name try replaceing it with a dash "-". 

Hope this helps

---

