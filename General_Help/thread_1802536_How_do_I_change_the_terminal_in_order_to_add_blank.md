---
title: "How do I change the terminal in order to add blank lines between commands?"
date: 2011-07-12
forum: General Help
---

### Post by rihard_marius on 2011-07-12
I'm studying C, and when I compile and run a file it looks like this

```
rihard@Toshiba:~$ ./pepe
Posicion actual de aptr_ch: 0x30fff4
Posicion despues de  aptr_ch + 1: 0x30fff5
Posicion despues de  aptr_ch + 2: 0x30fff6
Posicion despues de  aptr_ch - 1: 0x30fff3
Posicion despues de  aptr_ch - 2: 0x30fff2
Posicion actual de aptr_int: 0x804854b
Posicion despues de  aptr_int + 1: 0x804854f
Posicion despues de  aptr_int + 2: 0x8048553
Posicion despues de  aptr_int - 1: 0x8048547
Posicion despues de  aptr_int - 2: 0x8048543
Posicion actual de aptr_db: 0x953a50
Posicion despues de  aptr_db + 1: 0x953a58
Posicion despues de  aptr_db + 2: 0x953a60
Posicion despues de  aptr_db - 1: 0x953a48
Posicion despues de  aptr_db - 2: 0x953a40
rihard@Toshiba:~$       


```and I want it to look like this

```
rihard@Toshiba:~$ ./pepe

Posicion actual de aptr_ch: 0x30fff4
Posicion despues de  aptr_ch + 1: 0x30fff5
Posicion despues de  aptr_ch + 2: 0x30fff6
Posicion despues de  aptr_ch - 1: 0x30fff3
Posicion despues de  aptr_ch - 2: 0x30fff2
Posicion actual de aptr_int: 0x804854b
Posicion despues de  aptr_int + 1: 0x804854f
Posicion despues de  aptr_int + 2: 0x8048553
Posicion despues de  aptr_int - 1: 0x8048547
Posicion despues de  aptr_int - 2: 0x8048543
Posicion actual de aptr_db: 0x953a50
Posicion despues de  aptr_db + 1: 0x953a58
Posicion despues de  aptr_db + 2: 0x953a60
Posicion despues de  aptr_db - 1: 0x953a48
Posicion despues de  aptr_db - 2: 0x953a40

rihard@Toshiba:~$       


```just like that...

Thanks

---

### Post by nothingspecial on 2011-07-12
I don't know the first thing about C, but to print a blank line (or new line) in a bash terminal you can use a backslash escapes

So, try

```
./pepe; echo -e "\n"
```

Don't know if that's what you are looking for.

---

### Post by Vaphell on 2011-07-12
he could add printf("\n") to his code to achieve the same effect.

i think he wants to modify prompt to add empty line before and after.
open .bashrc and modify PS1 variable that describes the prompt - i think it should be possible to add newline before it (\n) but i don't see what to do to add newline automatically between command and its output.

---

### Post by rihard_marius on 2011-07-13
**NothingSpecial:**

with this code

```
./pepe; echo -e "\n"
```I got this output

```
rihard@Toshiba:~/C$ ./pepe; echo -e "\n"
Posicion actual de aptr_ch: 0x5d5ff4
Posicion despues de  aptr_ch + 1: 0x5d5ff5
Posicion despues de  aptr_ch + 2: 0x5d5ff6
Posicion despues de  aptr_ch - 1: 0x5d5ff3
Posicion despues de  aptr_ch - 2: 0x5d5ff2
Posicion actual de aptr_int: 0x804854b
Posicion despues de  aptr_int + 1: 0x804854f
Posicion despues de  aptr_int + 2: 0x8048553
Posicion despues de  aptr_int - 1: 0x8048547
Posicion despues de  aptr_int - 2: 0x8048543
Posicion actual de aptr_db: 0xe54a50
Posicion despues de  aptr_db + 1: 0xe54a58
Posicion despues de  aptr_db + 2: 0xe54a60
Posicion despues de  aptr_db - 1: 0xe54a48
Posicion despues de  aptr_db - 2: 0xe54a40


rihard@Toshiba:~/C$

```thanks anyway

**Vaphell:**

that's exactly what I want (modify prompt to add empty line before and after).
I opened the bashrc, and there are several ps1 variables,
besides I don't understand how to edit that, don't know the p language,
and I don't want to screw up the terminal.

I think I'll download the code::blocks ide...

or the following code, it's a bit long and complicated but it works

```
echo -e "\n"; ./pepe; echo -e "\n"
```Output:

```
rihard@Toshiba:~/C$ echo -e "\n"; ./pepe; echo -e "\n"


Posicion actual de aptr_ch: 0x4bfff4
Posicion despues de  aptr_ch + 1: 0x4bfff5
Posicion despues de  aptr_ch + 2: 0x4bfff6
Posicion despues de  aptr_ch - 1: 0x4bfff3
Posicion despues de  aptr_ch - 2: 0x4bfff2
Posicion actual de aptr_int: 0x804854b
Posicion despues de  aptr_int + 1: 0x804854f
Posicion despues de  aptr_int + 2: 0x8048553
Posicion despues de  aptr_int - 1: 0x8048547
Posicion despues de  aptr_int - 2: 0x8048543
Posicion actual de aptr_db: 0x73ca50
Posicion despues de  aptr_db + 1: 0x73ca58
Posicion despues de  aptr_db + 2: 0x73ca60
Posicion despues de  aptr_db - 1: 0x73ca48
Posicion despues de  aptr_db - 2: 0x73ca40


rihard@Toshiba:~/C$ 

```

Thanks everybody!

---

### Post by nothingspecial on 2011-07-13
You could add a function to your .bashrc

eg

```
blah () {
        echo -e "\n"; "$1"; echo -e "\n"
}
```


Then name of the function here is blah, but you call it whatever you like. The "$1" signifies the first argument to blah, which will be whatever C thing you want to run (or any command for that matter). 

Put it at the end of your .bashrc then type ```
. ~/.bashrc
``` so bash reads the modified file, then type

```
blah ./pepe
```

eg

```
ns@netbook\:~$ blah ls


Desktop    Downloads  mail   Pictures  Ubuntu One
Documents  Images     Music  source    Videos


ns@netbook\:~$ blah df


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             16654724   3365604  12443092  22% /
none                    500600       668    499932   1% /dev
none                    507224     14412    492812   3% /dev/shm
none                    507224       144    507080   1% /var/run
none                    507224         0    507224   0% /var/lock
/dev/sda1            136159400   1687112 127555732   2% /media/Data
/dev/sdb1              1955520   1766912    188608  91% /media/E0FD-1813


ns@netbook\:~$ 
```

Bear in mind, as it is, blah will only take one argument. So you cannot use it with a command that takes an argument itself. But it will work to run your own scripts/programs.

Hopefully that will help a little more.

---

### Post by rihard_marius on 2011-07-14
> **nothingspecial said:**
> You could add a function to your .bashrc

eg

```
blah () {
        echo -e "\n"; "$1"; echo -e "\n"
}
```
Then name of the function here is blah, but you call it whatever you like. The "$1" signifies the first argument to blah, which will be whatever C thing you want to run (or any command for that matter). 

Put it at the end of your .bashrc then type ```
. ~/.bashrc
``` so bash reads the modified file, then type

```
blah ./pepe
```eg

```
ns@netbook\:~$ blah ls


Desktop    Downloads  mail   Pictures  Ubuntu One
Documents  Images     Music  source    Videos


ns@netbook\:~$ blah df


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             16654724   3365604  12443092  22% /
none                    500600       668    499932   1% /dev
none                    507224     14412    492812   3% /dev/shm
none                    507224       144    507080   1% /var/run
none                    507224         0    507224   0% /var/lock
/dev/sda1            136159400   1687112 127555732   2% /media/Data
/dev/sdb1              1955520   1766912    188608  91% /media/E0FD-1813


ns@netbook\:~$ 
```Bear in mind, as it is, blah will only take one argument. So you cannot use it with a command that takes an argument itself. But it will work to run your own scripts/programs.

Hopefully that will help a little more.

It helped a lot.
Thank you very much NothingSpecial. O:)

P.S. What language has the bashrc?

---

### Post by nothingspecial on 2011-07-14
> **rihard_marius said:**
> 

P.S. What language has the bashrc?

er..... bash.....

which is not a language, more a way of interacting with your system. It has a syntax and some inbuilt commands but  it is not a programming language.

This explains it.

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

