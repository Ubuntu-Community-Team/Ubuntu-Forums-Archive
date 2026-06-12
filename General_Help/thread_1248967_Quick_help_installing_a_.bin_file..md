---
title: "Quick help installing a .bin file."
date: 2009-08-24
forum: General Help
---

### Post by Mad dog on 2009-08-24
I'm using Ubuntu 9.04. I entered:

```
sudo chmod +x /home/chris/Desktop/PT.bin
```

My output is absolutely nothing. The terminal just goes to a new line and nothing happens. Am I doing something wrong? The file is named PT.bin and it's sitting on my desktop.

---

### Post by Moop on 2009-08-24
If you didn't get a error message then it worked. The terminal doesn't tell you "mission accomplished." :)

---

### Post by tuxxy on 2009-08-24
> **Mad dog said:**
> I'm using Ubuntu 9.04. I entered:

```
sudo chmod +x /home/chris/Desktop/PT.bin
```My output is absolutely nothing. The terminal just goes to a new line and nothing happens. Am I doing something wrong? The file is named PT.bin and it's sitting on my desktop.

The command you entered didn't run the .bin it simply modified its permissions which you do before running the script.

So you would first do the chmod,
```

chmod  +x /home/chris/Desktop/PT.bin
```and then cd to your desktop and run it by entering,

```
./PT.bin

```

---

### Post by Mad dog on 2009-08-24
Haha :). I just expected to see some action. Okay, so next I tried: ```
sudo ./home/chris/Desktop/PT.bin
```

The output said "command does not exist." Did the new executable move somewhere else or is it called something else?

---

### Post by tuxxy on 2009-08-24
> **Mad dog said:**
> Haha :). I just expected to see some action. Okay, so next I tried: ```
sudo ./home/chris/Desktop/PT.bin
```The output said "command does not exist." Did the new executable move somewhere else or is it called something else?

You will see some action, you will see the script run in terminal.  Did you read my post above I just explained how to install the .bin

---

### Post by tuxxy on 2009-08-24
The 3 commands you need to run are in this order;

```
chmod  +x /home/chris/Desktop/PT.bin
``````
cd  /home/chris/Desktop
``````
./PT.bin
```

---

### Post by Mad dog on 2009-08-24
> **tuxxy said:**
> You will see some action, you will see the script run in terminal.  Did you read my post above I just explained how to install the .bin
I did. I'm sorry, I just don't know what "cd to your desktop" means. I thought I was doing it all right.

---

### Post by Mad dog on 2009-08-24
Thank you.

---

### Post by tuxxy on 2009-08-24
No problem, yes sorry my mistake I realised you may not have understood what I meant about cd to desktop hehe, at least you wont get stuck with .bins again :D

---

### Post by Mad dog on 2009-08-24
Yes. This is great basic info. I just did it and got it to work!

---

### Post by tuxxy on 2009-08-24
Cool hope you enjoy it :D if you get stuck in future this is a good page which explains how to install the various types.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

