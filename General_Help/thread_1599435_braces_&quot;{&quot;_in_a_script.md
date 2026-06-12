---
title: "braces &quot;{&quot; in a script?"
date: 2010-10-17
forum: General Help
---

### Post by leesiulung on 2010-10-17
I have the following code in a script

```

#!/bin/sh
clear
read domainname
read subdomainname
mkdir -p /var/www/$domainname/$subdomainname/{public,private,log,cgi-bin,backup,ssl,php-fcgi}

```Unfortunately, instead of making separate directoris for public, private, log, cgi-bin, backup, ssl and php-fcgi, it instead makes ONE directory named "{public,private,log,cgi-bin,backup,ssl,php-fcgi}". 

How can I accomplish this task with one line?

---

### Post by sisco311 on 2010-10-17
Not sure if/how you can do it dash (the default system shell in Ubutnu, see [uwiki]DashAsBinSh[/uwiki]), but your code should work just fine in bash. ;)

```
#!/bin/bash
...

```

---

### Post by leesiulung on 2010-10-17
> **sisco311 said:**
> Not sure if/how you can do it dash (the default system shell in Ubutnu, see [uwiki]DashAsBinSh[/uwiki]), but your code should work just fine in bash. ;)

```
#!/bin/bash
...

```

I'm sorry, I'm all confused. So the code should work fine?

It doesn't work for me at least. Maybe it is a configuration issue?

---

### Post by sisco311 on 2010-10-17
> **leesiulung said:**
> I'm sorry, I'm all confused. So the code should work fine?

It doesn't work for me at least. Maybe it is a configuration issue?

My bad. I wasn't clear enough. The code should work in bash but you run it in dash (in Ubuntu /bin/sh is a symlink to dash). You have to replace the first line (a.k.a [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)") ) in your script with:
```
#!/bin/bash
```

---

### Post by btindie on 2010-10-17
By default Ubuntu uses a shell called DASH, the more common one is called BASH. There are slight differences between them. The line of code you are using should work fine with BASH. To do so you need to change the first line of your code from ```
#!/bin/sh
``` to ```
#!/bin/bash
``` this is because /bin/sh is a symlink to /bin/dash and you need to use /bin/bash!

---

### Post by leesiulung on 2010-10-17
> **btindie said:**
> By default Ubuntu uses a shell called DASH, the more common one is called BASH. There are slight differences between them. The line of code you are using should work fine with BASH. To do so you need to change the first line of your code from ```
#!/bin/sh
``` to ```
#!/bin/bash
``` this is because /bin/sh is a symlink to /bin/dash and you need to use /bin/bash!

But changing the shell from Dash to Bash, doesn't that mean other parts of my code might break?

What is the default shell on Ubuntu Server if you just login from a clean installation?

---

### Post by btindie on 2010-10-17
If you read the link that was provided in post #2 you will see that they are different things. The login shell is BASH while /bin/sh which is DASH is used to execute shell scripts. You can see which one /bin/sh links to with
```
ls -l /bin/sh
```
Changing from DASH to BASH won't break any parts of your code, BASH supports everything DASH does and more (*I think*). It's a lot heavier which is why DASH is used by default as it will fill most needs.

If you try the command that failed from the terminal you'll see that it works, that's because it's using BASH. Though from a shell script using /bin/sh it won't work as it's using DASH.

Have a read of the link provided in post #2.

---

### Post by leesiulung on 2010-10-18
> **btindie said:**
> If you read the link that was provided in post #2 you will see that they are different things. The login shell is BASH while /bin/sh which is DASH is used to execute shell scripts. You can see which one /bin/sh links to with
```
ls -l /bin/sh
```Changing from DASH to BASH won't break any parts of your code, BASH supports everything DASH does and more (*I think*). It's a lot heavier which is why DASH is used by default as it will fill most needs.

If you try the command that failed from the terminal you'll see that it works, that's because it's using BASH. Though from a shell script using /bin/sh it won't work as it's using DASH.

Have a read of the link provided in post #2.

Ah, I didn't see the link. It was all black like the rest of the text. After reading the link and the explanation here, it now makes more sense.

I will give the bash shell a try. Thanks guys!

---

### Post by leesiulung on 2010-10-19
> **btindie said:**
> If you read the link that was provided in post #2 you will see that they are different things. The login shell is BASH while /bin/sh which is DASH is used to execute shell scripts. You can see which one /bin/sh links to with
```
ls -l /bin/sh
```Changing from DASH to BASH won't break any parts of your code, BASH supports everything DASH does and more (*I think*). It's a lot heavier which is why DASH is used by default as it will fill most needs.

If you try the command that failed from the terminal you'll see that it works, that's because it's using BASH. Though from a shell script using /bin/sh it won't work as it's using DASH.

Have a read of the link provided in post #2.

So I thought I report back. My results are that the code partly broke i.e. my echo's had formatting in it using escaped newlines '\n' and that no longer work in bash.

I just ended up splitting the mkdir statement into multiple statements.....

---

### Post by btindie on 2010-10-19
> **leesiulung said:**
> So I thought I report back. My results are that the code partly broke i.e. my echo's had formatting in it using escaped newlines '\n' and that no longer work in bash.
What are the echo commands you are trying to use that didn't work under BASH?

Something like?
```
echo -e "Line 1\nLine 2\nLine 3"
```

---

### Post by leesiulung on 2010-10-19
> **btindie said:**
> What are the echo commands you are trying to use that didn't work under BASH?

Something like?
```
echo -e "Line 1\nLine 2\nLine 3"
```

It was more like this

```

echo "Line 1\nLine2\n\Line 3..."

```

---

### Post by sisco311 on 2010-10-19
> **leesiulung said:**
> It was more like this

```

echo "Line 1\nLine2\n\Line 3..."

```

yep, the echo builtin in dash  interprets backslash-escaped characters by default, while in bash you have to use the -e flag.

See:
```
man dash | less +/" echo "
man bash | less +/" echo "
```

---

