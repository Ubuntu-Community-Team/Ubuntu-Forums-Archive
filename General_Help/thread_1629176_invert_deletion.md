---
title: "invert deletion"
date: 2010-11-23
forum: General Help
---

### Post by sukhdeepsingh on 2010-11-23
Hi, 
I was thinking as we have an option for invert selection , is there any option for invert deletion from command line.
We can invert select and then pass the output to deletion, but i dont know how to invert select from the command line.

Thanks
Regards,

Sukhdeep Singh

---

### Post by asmoore82 on 2010-11-23
almost all shells support a "range of letters" matching which is easily inverted with a `!` ...

```
[COLOR="Blue"]#show all files beginning with a, b, c, or d[/COLOR]
echo [abcd]*

[COLOR="Blue"]#show all files ending with n through z[/COLOR]
echo *[n-z]

[COLOR="Blue"]#show all files **not** beginning with a, b, c, d, or z[/COLOR]
echo [!a-dz]*

[COLOR="Blue"]#show all files **not** ending in an uppercase letter[/COLOR]
echo *[!A-Z]
```

Newer versions of BASH also support inverting a "glob" or "wildcard" match:
```
[COLOR="Blue"]#show all .odt files[/COLOR]
echo *.odt

[COLOR="Blue"]#show all files **except** .mp3's[/COLOR]
echo !(*.mp3)
```

---

### Post by sukhdeepsingh on 2010-11-23
Thats cools:D
Can you also tell you can I send this output to another command.
I seen some codes so working like 

```
myvar= echo [!pgt]*; du -hs $myvar
```

but I dont want to make another variable and use it again.
Just wanted to send the direct output.

Cheers

---

### Post by asmoore82 on 2010-11-24
The straightforward nature of shell scripting is often confusing at first.

All other programming languages give you the primitive tools to build up to do great and useful things. With a shell, the tools to do things already exist, the shell optimizes the act of calling them up and gluing them together.

For example, to call an external command from a "real" programming language, you must invoke some "execute" system call manually and reference the program as a string value of its full path:
```
[COLOR="Cyan"]/* pseudo programming language - Not shell code */[/COLOR]
exec([COLOR="Purple"]"/usr/bin/md5sum"[/COLOR])[COLOR="Red"];[/COLOR]
```
But with a shell, you simply type the program name, the shell resolves it to a full path, and diligently performs the system call silently:
```
[COLOR="Blue"]#Shell[/COLOR]
md5sum
```

Another prime example, for "real" programming, concatenating string values must be broken into the more primitive action, such as "addition":
```
[COLOR="Cyan"]/* pseudo programming language - Not shell code */[/COLOR]
name = [COLOR="Purple"]"Adam"[/COLOR][COLOR="Red"];[/COLOR]

print([COLOR="Purple"]"Hello, my name is "[/COLOR] + name + [COLOR="Purple"]"."[/COLOR])[COLOR="Red"];[/COLOR]
```

To make matters worse, rigidly structured programming languages can further confuse such an action into a proper function call, making deciphering it even more difficult at first glance:
```
[COLOR="Cyan"]/* pseudo programming language - Not shell code */[/COLOR]
stringCopy(name, [COLOR="Purple"]"Adam"[/COLOR])[COLOR="Red"];[/COLOR]

print([COLOR="Purple"]"Hello, my name is %s."[/COLOR], name)[COLOR="Red"];[/COLOR]
```

For the shell, however, text manipulation flows naturally:
```
[COLOR="Blue"]#Shell[/COLOR]
name=[COLOR="Purple"]"Adam"[/COLOR]

echo [COLOR="Purple"]"Hello, my name is [COLOR="Red"]$name[/COLOR]."[/COLOR]
```

And finally (sorry for being long winded), we come to your situation. You can simply flow in the shell's processing abilities with your external command calls. As your shell commands become more advanced, it becomes important to note that the shell's text manipulation is performed entirely *before* any external commands are called. Also, shell variable references should always be quoted but not wildcards, or they lose their special meaning:
```
[COLOR="Blue"]#Shell[/COLOR]
du -sh [!pgt]*

[COLOR="Blue"]#Variables flow in with commands naturally.[/COLOR]
folder="Pictures"
du -sh "$folder"

[COLOR="Blue"]#But only variable references should be quoted.[/COLOR]
ext=".mp3"
du -sh *"$ext"

[COLOR="Blue"]#"Except" example[/COLOR]
du -sh !(*"$ext")
```

---

### Post by JoelOl75 on 2010-11-24
To use the output in another command there's a couple ways... The most common I see is to place the command into backticks where you want the output to be...

echo "The Directory you are in is `pwd`"

Also you can pipe the output of a command into the input of another.

cat /var/log/messages|less

notice the last command can just be shortened to

less /var/log/messages

but I just wanted to make a point...

---

### Post by sukhdeepsingh on 2010-11-24
Thanks @asmoore82
for the exhaustive answer. It explained the shell working.

Thanks @JoelOl75
for the quick message, its of great use.

Regards,
Sukhdeep Singh:p

---

