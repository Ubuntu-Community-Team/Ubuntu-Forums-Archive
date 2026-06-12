---
title: "Finding String in Terminal"
date: 2010-04-13
forum: General Help
---

### Post by Elie-M on 2010-04-13
when using the terminal several hundreds of lines are generated. we need to find some strings in these lines to work (for example I need to find a user mac address to know what's his signal). the thing is terminal doesnt have an apparent on-the-spot find/search option to search the terminal command output. what I'm asking for is an option similar to the dos function, and that's what is keeping my boss from using ubuntu.

Screeshot 1 is an what the actual case is: [http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1-1.png](http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1-1.png)

Screenshot 2 is an edited image of what I need: [http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-2.png](http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-2.png)

when using telnet u need a right click option to find strings, cz any command will be taken as an IOS command not linux

---

### Post by Elie-M on 2010-04-13
bump.. sry but I need an answer

---

### Post by Vaphell on 2010-04-13
[http://ubuntuforums.org/showthread.php?t=340043](http://ubuntuforums.org/showthread.php?t=340043)

besides searching in the raw output in terminal is a little messy solution. You can always redirect command output to the file to achieve persistence (terminal buffer is limited) and then use any search tools you can dream of.

---

### Post by Elie-M on 2010-04-14
well redirecting the output and search isnt very handy and fast in work. when u work and u lookup signals u need speed searching, the windows dos interface gives u the option to search, I dunno why linux doesnt............. I'm trying to convince them to switch to linux but they are sticking in windows just bcz of this...

---

### Post by capybara! on 2010-04-14
Isn't grep exactly what you need?
```
command | grep pattern
```
shows you only the output from your command which contains pattern.
With grep -B and the number of lines you can also output lines before the line the pattern was in and with grep -A some lines after...

Hope this helps...

---

### Post by Elie-M on 2010-04-14
it's true u can do that in terminal and get the result. but go do telnet to some windows pc or Cisco IOS and try to use grep. Result: "Command Not found" "Bad Command"

got my idea?


anyways the guyz that works there doesnt know anything abt linux and telling them to use a command on every search is a bit of an exageration in my opinion

---

### Post by prodigy_ on 2010-04-14
> **Elie-M said:**
> it's true u can do that in terminal and get the result. but go do telnet to some windows pc or Cisco IOS and try to use grep. Result: "Command Not found" "Bad Command"
Naturally, when you run commands on a remote system you're limited by searching facilities this system provides. For Windows, that's **find** or **findstr** command, for Cisco IOS - **show** and **include/exclude** commands:
[http://www.cisco.com/en/US/docs/ios/12_3t/12_3t2/feature/guide/gtshfltr.html#wp1027129](http://www.cisco.com/en/US/docs/ios/12_3t/12_3t2/feature/guide/gtshfltr.html#wp1027129)

> **Elie-M said:**
> anyways the guyz that works there doesnt know anything abt linux
Seems they don't know anything about Windows or IOS either. Maybe they need a refresher course? ;-)

Speaking seriously, you might want to look for a more advanced telnet client. I know for sure that SecureCRT allows you to search terminal buffer using GUI. It's a Windows program though.

---

### Post by Elie-M on 2010-04-15
yeah they dont know linux. i want to teach them linux step by step but it's ridiculous to tell them this is the terminal work with it... we'll start GUI then a little deeper.

but here's  a screenshot I included that shows the find function of windows finding a string for u in a telnet IOS environment. this is what I need in linux:

[http://i156.photobucket.com/albums/t18/Mankind-195/Untitled-1.jpg](http://i156.photobucket.com/albums/t18/Mankind-195/Untitled-1.jpg)

---

### Post by kellemes on 2010-04-15
I don't use Gnome-Terminal but I use Konsole.
It has exactly what you need, Ctrl-Shift-F..

[http://imm.io/jPm]("http://imm.io/jPm")

---

### Post by aeiah on 2010-04-15
gnu screen will do this, and you can use gnu screen within any shell or terminal emulator. it may confuse them though. you have to enter scrollback mode:
```

C-a[

```
then ? to search back and / to search forward

---

### Post by Elie-M on 2010-04-15
thx for the suggestions I'll go try them and reply ;)

Edit: Konsole is THE Key! U're man :D   Solved!

---

