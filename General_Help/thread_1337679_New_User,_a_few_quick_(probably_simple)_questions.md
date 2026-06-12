---
title: "New User, a few quick (probably simple) questions"
date: 2009-11-25
forum: General Help
---

### Post by JustinNotJason on 2009-11-25
Hey I just installed Ubuntu on my laptop (been meaning too) and a few quick questions. 

-My temps are kind've high in Ubuntu. In Win 7 I can get low 40's - mid 50's (celcius) while idling or doing light work. 
In ubuntu I'm not seeing sub 60C. It's been going at 61-63c.
Any Ideas? (I'm using GNOME Sensors Applet 2.2.3 to monitor)

-Any good apps to measure CPU usage? 

- And is Ubuntu a good distro to start with to learn the in's and out's of linux. My ture intention is to become adept at using Linux since I like the idea behind it and what not, and  also I'm a bit of a computer junkie, but up until now mostly windows and hardware in general.

Alright any help is greatly appreciated.

---

### Post by audiomick on 2009-11-25
> **JustinNotJason said:**
> Hey I just installed Ubuntu on my laptop (been meaning too) and a few quick questions. 
Good man! I'm not an expert, but here my 2 bib's worth:

```
-My temps are kind've high in Ubuntu. In Win 7 I can get low 40's - mid 50's (celcius) while idling or doing light work. 
In ubuntu I'm not seeing sub 60C. It's been going at 61-63c.
Any Ideas? (I'm using GNOME Sensors Applet 2.2.3 to monitor)

```
At a guess, the CPU or fan regulation is not working as well as in windows. You get that. There's heaps of info on the subject around, but I can't say much about it because I haven't looked into it

> -Any good apps to measure CPU usage? 

Try the one that is installed. ;)It is not that precise, but is enough to let you know what is happening. It is in 
system >administration> (systemüberwachung) probably system monitor

My computer speaks German for my girlfriend's benifit, and I don't know what half of these menu items are in english:oops:. Anyway, you'll know it when you see it.

> - And is Ubuntu a good distro to start with to learn the in's and out's of linux. My ture intention is to become adept at using Linux since I like the idea behind it and what not, and  also I'm a bit of a computer junkie, but up until now mostly windows and hardware in general.
 
I am converted. ;) Ubuntu is great, easy to use, works nearly all the time ( better track record for me than windows... ). The only thing you should be aware of, is that root is by default disabled in Ubuntu. If you don't know about root yet, you will as yoon as you start learning about linux. Root is like the administrator in a windows system. It is disabled in Ubuntu to make the system user friendly. All the stuff you need to do as root gets done using the sudo command. That threw me at first, after coming from a suse system, but now I find it better.

Hope that helps.
Michael

---

### Post by juancarlospaco on 2009-11-25
For Temp. [sudo apt-get install acpi]("apt:/acpi")
:)

---

### Post by audiomick on 2009-11-25
> **juancarlospaco said:**
> For Temp. [sudo apt-get install acpi]("apt:/acpi")
:)

That's the power management thingy

---

### Post by soni1770 on 2009-11-25
conky's pretty cool,

you can measure all sorts of stuff with that,

---

### Post by ikacer on 2009-11-25
The temperatures should not be that high. Your CPU can be monitored with
System -> Administration -> System Monitor
or, in a terminal by typing ```
top
```

If your cpu is working too much (which could be the cause of the temperatures), it might be because of missing video drivers. if so go to:
System -> Administration -> Hardware Drivers

As for a good system monitor, the best one is definitely Conky. However Conky, which is highly customisable, is not entirely user friendly, as you have to write a configuration file (see [here)]("http://ubuntuforums.org/showthread.php?t=281865"). Other good choices are "top", and "gnome-system-monitor".


Also, Ubuntu is a great choice as your first Linux distro. If you haven't already, I suggest you enable the universe and multiverse repositories in your software sources and add Medibuntu ([http://www.medibuntu.org/]("http://www.medibuntu.org/")).

Cheers.

---

### Post by JustinNotJason on 2009-11-25
> **audiomick said:**
> 
I am converted. ;) Ubuntu is great, easy to use, works nearly all the time ( better track record for me than windows... ). The only thing you should be aware of, is that root is by default disabled in Ubuntu. If you don't know about root yet, you will as yoon as you start learning about linux. Root is like the administrator in a windows system. It is disabled in Ubuntu to make the system user friendly. All the stuff you need to do as root gets done using the sudo command. That threw me at first, after coming from a suse system, but now I find it better.

Hope that helps.
Michael

Yeah I've been messing around. sudo and root and what have you. I like it. It makes more sense for security.

> **ikacer said:**
> The temperatures should not be that high. Your CPU can be monitored with
System -> Administration -> System Monitor
or, in a terminal by typing ```
top
```If your cpu is working too much (which could be the cause of the temperatures), it might be because of missing video drivers. if so go to:
System -> Administration -> Hardware Drivers

As for a good system monitor, the best one is definitely Conky. However Conky, which is highly customisable, is not entirely user friendly, as you have to write a configuration file (see [here)]("http://ubuntuforums.org/showthread.php?t=281865"). Other good choices are "top", and "gnome-system-monitor".


Also, Ubuntu is a great choice as your first Linux distro. If you haven't already, I suggest you enable the universe and multiverse repositories in your software sources and add Medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/)).

Cheers.

What is Medibuntu exactly?

And also my CPU usage bounces between 10 - 25% when Idling which is about what I got in windows. Basically the fan on my laptop is on constantly and temps are bouncing in the 60's C. So gotta look at that fan regulation thing.



As for right now I'm on a mission to get access back to my Win 7 partition. I knew that it'd get messed up when dual booting ( expereince :neutral:) but I didn't realize my recovery CD wouldn't repair the MBR. 

So I'm checking that out at the moment. Particularly SuperGrub.

---

### Post by audiomick on 2009-11-25
> **JustinNotJason said:**
> 
What is Medibuntu exactly?

> from [www.medibuntu.org](www.medibuntu.org)
Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues.

this is also helpful:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by JustinNotJason on 2009-11-25
Is there any reason in particular that it takes forever for ubuntu to connect to my network. It's hidden and even if I save it it doesn't automatically connect.

I have to go in and reconfigure it ever time.

---

