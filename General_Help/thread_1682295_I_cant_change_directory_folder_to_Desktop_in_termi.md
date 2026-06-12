---
title: "I cant change directory folder to Desktop in terminal"
date: 2011-02-05
forum: General Help
---

### Post by Outspacer on 2011-02-05
Hello everyone.
I run Ubuntu 10.10. and I  have one annoying problem. When I want to set my Desktop directory in terminal by typing this: "**cd ~/Desktop**" 
I get an error:                                                                                                
"**bash: cd: /home/izvanzemaljac/Desktop: No such file or directory**".
I really dont know what to do, I checked Google for this error and I didnt find a solution.
Thx in advance.

---

### Post by TheJackal12 on 2011-02-05
Try:
```
sudo su
cd /home/izvanzemaljac/Desktop
```

---

### Post by Outspacer on 2011-02-06
> **TheJackal12 said:**
> Try:
```
sudo su
cd /home/izvanzemaljac/Desktop
```

I am sorry but your code doesnt work. 
The error is the same like the previous one:
"**bash: cd: /home/izvanzemaljac/Desktop: No such file or directory**",
Any other solutions please?

---

### Post by Spyderkid on 2011-02-06
Copy and paste this to avoid mistakes:

```

cd Desktop

```

or 

```

cd home/izvanzemaljac/Desktop

```

dont add in / before home

---

### Post by whatthefunk on 2011-02-06
Try this

```
cd
```Hit enter and then do

```
cd Desktop/
```

Your problem may be that you dont have the / on the end of Desktop.  Its a directory so you need to include this.

---

### Post by Vaphell on 2011-02-06
don't you use ubuntu in your language of choice? Your name suggests some south-slavic language and most probably your Desktop folder has its name translated (e.g. in Polish version Desktop is called Pulpit).
run ls ~ to list contents of your home directory and look for something that is a direct translation of 'desktop' word and use it instead of english Desktop.

---

### Post by Outspacer on 2011-02-06
> **Vaphell said:**
> don't you use ubuntu in your language of choice? Your name suggests some south-slavic language and most probably your Desktop folder has its name translated (e.g. in Polish version Desktop is called Pulpit).
run ls ~ to list contents of your home directory and look for something that is a direct translation of 'desktop' word and use it instead of english Desktop.

Thank you for your advice, it worked. I was using Croatian language pack but then I set English as my default language and I was able to change directory to the Desktop.

---

