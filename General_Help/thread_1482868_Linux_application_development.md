---
title: "Linux application development"
date: 2010-05-14
forum: General Help
---

### Post by warri0r on 2010-05-14
hey folks,
basically i m a computer science student, i m using this debian and ubuntu quiet few years and now i m able to get rid of windows and move completely to linux. i have plans on developing a small application for ubuntu, apart from shell scripting what is the programming language tat i need to learn for developing a gui application, something like simple app like tasque.

i know c, cpp, core java, basics of shell scripting, php. Need suggestions. thanks

---

### Post by devilized on 2010-05-14
Python can make some pretty cool applications in Linux. I've heard a lot about the WxWidgets being rather popular. Check out: [http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming)

---

### Post by warri0r on 2010-05-17
well, isnt tat i can do things with c? is python more easier than tat?

any suggestions welcomed :)

---

### Post by NexusZA on 2010-05-17
Python is a lot simpler than c and c++ yes, but it depends on what you want. C and C++ offer better performance because they are a bit lower level than Python (i.e. closer to hardware layer) but if ease and speed of development are more important to you and not uber performance of your application then Python is a very viable option. Its all about picking the right language for you.

For example, if you were going to be writing code that needs close association with the kernel and/or hardware layers, then C or C++ would be your best bet. If you were just writing a desktop application that would be accessing third-party libraries then Python might be a better option.

---

### Post by 3rdalbum on 2010-05-17
Python is excellent - most, if not all, Ubuntu-specific programs are written in Python.

It's quicker to write and easier to debug than C and C++, so for small programs and for times when you want a program as quickly as possible, it's ideal.

If you're going to be writing the next big commercial game, you need a high performance language like C, or if you want to write a kernel driver it has to be done in C. Otherwise, Python is really cool.

---

