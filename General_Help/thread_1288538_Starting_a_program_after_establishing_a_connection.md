---
title: "Starting a program after establishing a connection"
date: 2009-10-11
forum: General Help
---

### Post by ablom on 2009-10-11
I was just wondering if it's possible to start a program on startup in Jaunty after my wireless has connected. For example, I would like to start rainlendar2 after the internet connects because I have the weather feature enabled. I currently have a delay of 40 seconds on it (sh -c "sleep 40 && rainlendar2"), but I prefer it to start immediately after it connects to the internet and to not start until it does connect.

---

### Post by madsmeg on 2009-10-11
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=559435") post, it may help you write a script to check net connection and then launch your program.

EDIT: I would try and test it myself and write the script for you, but i am at work on a windows PC.

---

### Post by ablom on 2009-10-11
Madsmeg,thanks for the response. I looked over that post you provided, but, to be honest, I didn't really understand how to apply to a script. I'm very new to linux, which explains my confusion.

---

### Post by ablom on 2009-10-12
Ok, so I think I figured out how to do it, but i need some help writing the script. I think the best way would be to ping a server and then loop the script until it finds the server in which case the program will startup and the loop will end. I'm not exactly sure what commands to use though.

---

### Post by ablom on 2009-10-12
Here it is:
```
#! /bin/bash
while true
do

    if eval "ping -c 1 www.google.com"; then
        echo "Starting rainlendar"
        rainlendar2
        break
    else
     sleep 5
    fi

done
fi
```
If anyone can critique it, I 'd be grateful.

---

