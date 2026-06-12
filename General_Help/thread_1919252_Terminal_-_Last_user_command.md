---
title: "Terminal - Last user command"
date: 2012-02-02
forum: General Help
---

### Post by Owen r on 2012-02-02
Hi there,
            I've been using the 'last' command in the terminal. It can be used with the option '-t', but I can't seem to get the syntax right to show, say the last 7 days of login records. What's the correct format for this option? Can I use phrases as per other commands - like 'yesterday' etc?

---

### Post by drdos2006 on 2012-02-02
Use 'man last' for assistance.
'man' is short for the manual.

regards

---

### Post by Vaphell on 2012-02-02
you could do something like this:
```
last -t $( date -d '7 days ago' +%Y%m%d000000 )
```
but i dont think -t does what you think it does
[http://www.basicconfig.com/linux/last](http://www.basicconfig.com/linux/last)

> -t YYYYMMDDHHMMSS
    Display the state of logins as of the specified time. This is useful, e.g., to 
    determine easily who was logged in at a particular time -- specify that 
    time with -t and look for "still logged in". 
according to this, *last* doesn't show the history but the state at the time given.

I think you need to run *last* and process the output manually with a script.

---

### Post by Owen r on 2012-02-02
Thanks Vaphell, much appreciated.

---

### Post by jwbrase on 2012-02-02
Furthermore, when I run last, I get 

```

[Login information]

**wtmp begins Wed Feb  1 12:58:24 2012**

```

So it looks like Ubuntu is throwing wtmp information that's more than a day or so old. So you probably wouldn't be able to get a week's worth of login information without changing a setting somewhere to get Ubuntu to keep the information longer.

---

### Post by Vaphell on 2012-02-02
it appears that the wtmp file is rotated, there is an archive with wtmp.1 file inside and when you call **last -f wtmp.1** you get one month worth of data.

---

