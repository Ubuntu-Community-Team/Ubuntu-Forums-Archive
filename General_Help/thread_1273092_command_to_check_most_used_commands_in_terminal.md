---
title: "command to check most used commands in terminal?"
date: 2009-09-23
forum: General Help
---

### Post by abhilashm86 on 2009-09-23
when i just tried this to check most used commands, its showing some numericals, what is wrong? i want to see commands how many times its been used......```

history|awk '{print $2}'|awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c|sort -r
```

is there any package which shows most sommands used?
also are there any shell scripts or packages which enchances my terminal code completion?? even TAB is a great, just for info i asked.........

---

### Post by tgeer43 on 2009-09-23
When I run the same code it shows each command that I've used and how many times I've used it which sounds like just what you are looking for. What do you mean by, "some numericals"? Post the output of the command here.

tgeer

---

### Post by abhilashm86 on 2009-09-23
> **tgeer43 said:**
> When I run the same code it shows each command that I've used and how many times I've used it which sounds like just what you are looking for. What do you mean by, "some numericals"? Post the output of the command here.

tgeer
this is my output, 
```
abhilash@abhilash:~$ history|awk '{print $2}'|awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c|sort -r
      8 20:28
      8 19:40
      8 10:57
      7 22:10
      7 21:41
      7 21:40
      7 19:39
      7 19:38
      7 10:39
      6 22:17
      6 20:47
      6 20:32
      6 20:25
      6 19:11
      6 18:20
      6 10:42
      6 10:27
      6 08:12
      5 21:39
      5 20:51
      5 20:36
      5 20:22
      5 20:21
      5 20:16
      5 19:21
      5 19:13
      5 18:44
      4 22:16
      4 21:37
      4 21:02
      4 20:46
      4 20:45
      4 20:38
      4 20:35
      4 20:29
      4 20:05
      4 20:00
      4 19:36
      4 18:34
      4 10:12
      4 08:30
      4 08:27
      3 22:43
      3 22:41
      3 22:11
      3 20:55
      3 20:52
      3 20:39
      3 20:31
      3 20:30
      3 20:27
      3 19:58
      3 19:41
      3 18:33
      3 18:26
      3 18:21
      3 15:50
      3 10:58
      3 10:41
      3 10:37
      3 10:19
      3 07:36
      2 22:56
      2 22:40
      2 22:37
      2 22:36
      2 22:28
      2 22:20
      2 22:18
      2 22:12
      2 21:59
      2 21:58
      2 21:35
      2 21:01
      2 20:56
      2 20:33
      2 20:24
      2 20:17
      2 20:08
      2 20:07
      2 20:03
      2 19:59
      2 19:54
      2 19:50
      2 19:20
      2 19:19
      2 19:12
      2 18:43
      2 18:42
      2 18:25
      2 18:05
      2 14:58
      2 14:12
      2 11:07
      2 10:50
      2 10:25
      2 10:22
      2 08:33
      2 08:31
      2 08:17
     16 19:42
     16 10:18
      1 22:57
      1 22:44
      1 22:42
      1 22:39
      1 22:35
      1 22:22
      1 22:21
      1 22:19
      1 22:00
      1 21:55
      1 21:33
      1 21:22
      1 21:21
     12 10:38
      1 20:50
      1 20:49
      1 20:44
      1 20:34
      1 20:19
      1 20:04
      1 19:57
      1 19:52
      1 19:47
      1 19:37
      1 19:35
      1 19:30
      1 19:17
      1 19:15
      1 19:14
      1 18:52
      1 18:45
      1 18:40
      1 18:35
      1 18:27
      1 18:13
      1 18:08
      1 18:07
      1 17:02
      1 16:59
      1 16:58
      1 16:37
      1 16:14
      1 16:02
      1 15:57
      1 15:47
      1 14:57
      1 14:30
      1 14:13
      1 12:34
     11 22:15
     11 20:26
      1 11:56
      1 11:40
      1 11:21
      1 11:19
      1 10:47
      1 10:43
      1 10:26
      1 10:21
      1 08:46
      1 08:29
      1 08:18
      1 08:15
      1 07:37
      1 07:31
      1 07:23
     10 10:17
abhilash@abhilash:~$ 


```
why it dosen't show command name or is this wrong?

---

### Post by abhilashm86 on 2009-09-23
> **tgeer43 said:**
> When I run the same code it shows each command that I've used and how many times I've used it which sounds like just what you are looking for. What do you mean by, "some numericals"? Post the output of the command here.

tgeer


hey just show your output, i guess something wrong in this command........

---

### Post by tgeer43 on 2009-09-23
I thinks there's something wrong with the command too but nothing that explains your output. What is wrong is that it does not show each unique command in the history.

For your reference, here is a small section of my output:
```
      9 pactl
      7 cp
      6 tar
      6 ffmpeg
      5 iftop
      5 id
      5 exit
      5 bluemon
     56 man
     56 for
      4 python
      4 normalize-audio
      4 lame
      4 gpg
      4 aplay

```I suspect your history file is corrupted. What does the output look like if you just enter the command 'history'?

tgeer

---

### Post by dcstar on 2009-09-23
> **abhilashm86 said:**
> this is my output, 
```
abhilash@abhilash:~$ history|awk '{print $2}'|awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c|sort -r
      8 20:28
.......
     10 10:17
abhilash@abhilash:~$ 


```
why it dosen't show command name or is this wrong?

Because there is some other setting changing the default "history" output, post the following output:

```
history | tail
```

---

### Post by abhilashm86 on 2009-09-23
> **dcstar said:**
> Because there is some other setting changing the default "history" output, post the following output:

```
history | tail
```

is anything wrong with my .bash_history?? this is output, 
```
abhilash@abhilash:~$ history | tail
  597  11:26 > ifconfig 
  598  11:39 > netstat
  599  11:39 > man netstat 
  600  11:39 > nmap -sT -O localhost
  601  11:39 > sudo nmap -sT -O localhost
  602  11:40 > cat /etc/services | grep 834
  603  11:40 > netstat -anp | grep 834
  604  11:40 > sudo netstat -anp | grep 834
  605  11:40 > lsof -i | grep 834
  606  11:43 > history | tail
abhilash@abhilash:~$ 

```
is this correct, why i'm not getting proper results?

---

### Post by tgeer43 on 2009-09-23
My history does not show the time and looks like this:
```
   83  lsusb
   84  hardinfo
   85  lspci
   86  cat /proc/cpuinfo
   87  lspci
   88  lsagp
   89  cd Temp
   90  ls
   91  cd vumeter-0.9.2
   92  ls
   93  ./configure
   94  startx
```You just need to modify your awk command to parse the unneeded data out.

tgeer

---

### Post by geirha on 2009-09-23
According to «help history»:
```

    If the $HISTTIMEFORMAT variable is set and not null, its value is used
    as a format string for strftime(3) to print the time stamp associated
    with each displayed history entry.  No time stamps are printed otherwise.

```
So it appears that variable is set to something like «HISTTIMEFORMAT="%H:%M > "» for you.

Try running history with that variable set to empty.
```
HISTTIMEFORMAT= history|tail
```

---

### Post by abhilashm86 on 2009-09-23
> **geirha said:**
> According to «help history»:

Try running history with that variable set to empty.
```
HISTTIMEFORMAT= history|tail
```

yes i did, even now the output remains same........does any other application is meesing with this?

---

### Post by tgeer43 on 2009-09-23
Shouldn't be. How about trying:
```
HISTTIMEFORMAT=
export HISTTIMEFORMAT
```And then see what your output looks like.

tgeer

---

### Post by abhilashm86 on 2009-09-23
> **tgeer43 said:**
> Shouldn't be. How about trying:
```
HISTTIMEFORMAT=
export HISTTIMEFORMAT
```And then see what your output looks like.

tgeer

yes this did the work!! oh when we set env variables, we need to export:) thanks a lot:)
```
 9 nautilus
      9 man
     90 ls
      8 who
      8 mod
      8 feh
     72 cd
      6 whereis
      6 vim

```

---

### Post by tgeer43 on 2009-09-23
Always happy to help a fellow Ubuntian, err, Ubuntite, Ubuntuer? :wink:

tgeer

---

