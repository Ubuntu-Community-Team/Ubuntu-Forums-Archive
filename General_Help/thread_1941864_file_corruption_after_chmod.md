---
title: "file corruption after chmod"
date: 2012-03-16
forum: General Help
---

### Post by Zandro on 2012-03-16
Hi,

On my ubuntu 11.10 I tried to change the permissions of some files with the command: ```
chmod
```, but instead the files got corrupted.

Using the command ```
ls -l
``` to view the permissions I get
```

d????????? ? ? ? ?                ? dirname
-????????? ? ? ? ?                ? filename

```This files are webfiles residing within htdocs of the webserver Lampp.
I tried to change the permissions while the webserver Lampp was running, 
maybe because of that a conflict was generated.

Can I reverse the problem without the need to remove the files?

Thank you,
Zandro

---

### Post by codemaniac on 2012-03-16
Can you please post the exact **chmod **commandline that you have fired ?

---

### Post by Zandro on 2012-03-26
I simply used **chmod** like this:
```
sudo chmod -R 0666 htdocs
```

---

### Post by codemaniac on 2012-03-27
binary permissions bits are always of 3 characters long ,i.e 666 .
your commandline should look like 
```
sudo chmod -R **666 **htdocs
```

---

### Post by redmk2 on 2012-03-27
> **codemaniac said:**
> binary permissions bits are always of 3 characters long ,i.e 666 .
your commandline should look like 
```
sudo chmod -R **666 **htdocs
```

Nope, they're 4 bits long.  If you don't declare the leading bit then it is assumed to be 0.  The first bit (leading) is where you set the suid or sgid or sticky bit.  See [***[COLOR="Blue"]here[/COLOR]***]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for more info.

---

### Post by codemaniac on 2012-03-27
> **redmk2 said:**
> Nope, they're 4 bits long.  If you don't declare the leading bit then it is assumed to be 0.  The first bit (leading) is where you set the suid or sgid or sticky bit.  See [***[COLOR="Blue"]here[/COLOR]***]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for more info.

Thanks redmk2 for the enlightment .I thought they were only three chars long .Logically it should be 2^x(4 chars) long .
Thanks again for the info .

---

### Post by Zandro on 2012-03-29
I still don't know how to solve this.
I guess I will have to remove all corrupt files and install them again.

---

### Post by Zandro on 2012-03-29
Where does Ubuntu save the permissions of the files?
Maybe I can change the permissions by hand.

---

