---
title: "All my /home/* folders are owned by root!"
date: 2012-06-20
forum: General Help
---

### Post by AlexBooton on 2012-06-20
Hi,

I've set up a new 12.04 system partly by copying folders from the old system.

In the process, all my users' folders ended up owned by root!

Is there any way to reset ownership in bulk -- w/o having to do a separate chown for each user?

Thanks,

AB

---

### Post by HiImTye on 2012-06-20
you could try something like
```
for f in /home/*; do sed 's|/home/\(.*\)|chown -R \1 /home/\1|e'; done
```

---

### Post by SeijiSensei on 2012-06-20
That's a bit complex.  How about this?

```

sudo su -
[enter password]
cd /home
for U in *
do
   chown -R $U.$U $U
done
exit

```

The first line lets you run the remaining commands as root without dealing with sudo each time.

---

### Post by AlexBooton on 2012-06-20
Thank you both!

You saved me a lot of time and effort and probably avoided some mistakes.

Plus you taught me something useful.

For anyone else w/this issue, I used SeijiSensei approach only b/c it seemed a bit easier.

I appreciate it,

AB

---

### Post by ajgreeny on 2012-06-21
> **SeijiSensei said:**
> That's a bit complex.  How about this?

```

sudo su -
[enter password]
cd /home
for U in *
do
   [COLOR=Red]chown -R $U.$U $U[/COLOR]
done
exit

```The first line lets you run the remaining commands as root without dealing with sudo each time.
Just out of interest, why is there a . in the chown command not a : as there would normally be, ie,  [COLOR=Red]chown -R $U:$U $U[/COLOR]

---

### Post by dcottingham on 2012-06-21
Well, now I've learned something. I've always used user.group running chown, but I just did a "man chown" and it says you specify it as user:group. So apparently they both work. And just as apparently, I have never before read the man page for chown.

---

### Post by sisco311 on 2012-06-21
The period (`.') works in GNU chown for legacy reasons. Form **info coreutils 'chown invocation'**
```
[noparse]   Some older scripts may still use `.' in place of the `:' separator.
POSIX 1003.1-2001 (*note Standards conformance::) does not require
support for that, but for backward compatibility GNU `chown' supports
`.' so long as no ambiguity results.  New scripts should avoid the use
of `.' because it is not portable, and because it has undesirable
results if the entire OWNER`.'GROUP happens to identify a user whose
name contains `.'.[/noparse]

``` 

In Ubuntu, by default, /home only contains the home directories of normal users. And the name of the home directory is the same as the name of the user and its primary group. But this is only a default setting, so you can't rely on it. Assuming that we talk about potential home directories of local users, you have to check the entries /etc/passwd. In a POSIX shell, I'd try something like:
```

for file in /home/*
do
    while IFS=: read -r user _ uig gid _ home _
    do
        if [[ "$file" == "$home" ]]
        then
            echo chown -R "$user": "$home"
        fi
    done < /etc/passwd
done

```

NOTE: if the group after the colon is omitted, then the primary (login) group of the user is assumed.

---

### Post by ajgreeny on 2012-06-21
> **sisco311 said:**
> The period (`.') works in GNU chown for legacy reasons. Form **info coreutils 'chown invocation'**
```
[noparse]   Some older scripts may still use `.' in place of the `:' separator.
POSIX 1003.1-2001 (*note Standards conformance::) does not require
support for that, but for backward compatibility GNU `chown' supports
`.' so long as no ambiguity results.  New scripts should avoid the use
of `.' because it is not portable, and because it has undesirable
results if the entire OWNER`.'GROUP happens to identify a user whose
name contains `.'.[/noparse]

```In Ubuntu, by default, /home only contains the home directories of normal users. And the name of the home directory is the same as the name of the user and its primary group. But this is only a default setting, so you can't rely on it. Assuming that we talk about potential home directories of local users, you have to check the entries /etc/passwd. In a POSIX shell, I'd try something like:
```

for file in /home/*
do
    while IFS=: read -r user _ uig gid _ home _
    do
        if [[ "$file" == "$home" ]]
        then
            echo chown -R "$user": "$home"
        fi
    done < /etc/passwd
done

```NOTE: if the group after the colon is omitted, then the primary (login) group of the user is assumed.
Great!

Thanks for that info.

 I have always, but it seems unnecessarily so, put both user and group in any chown command I've used.  Still it does not seem to matter if I do that; it's just a belt and braces approach.

---

