---
title: "sed issue"
date: 2011-12-14
forum: General Help
---

### Post by Drenriza on 2011-12-14
Hi all.

I have the following command
```
sed '$text1s/.*/$replace/' testphpfil
```

$text1 = 116
$replace = #LoadModule php5_module        libexec/apache2/libphp5.so

to replace a line on line number 116.
But this just writes $replace and $text and not the value of $replace & $text. How can i correct that?

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2011-12-14
Use double quotes instead.

---

### Post by lechien73 on 2011-12-14
Also, add a space between $text1 and s.

Your final command should read:

```
sed "$text1 s/.*/$replace/" testphpfil
```

---

### Post by Drenriza on 2011-12-14
i tried with double quotas before but got an error so thought it was because of the double quotas.

copy pasted
```
sed "$text1 s/.*/$replace/" testphpfil
```

But the error i get is
sed: 1: "116 s/.*/LoadModule php ...": bad flag in substitute command: 'a'

---

### Post by lechien73 on 2011-12-14
Ah yes, forgot to mention - also enclose your variable declaration in double quotes, and escape the forward slashes so:

```
replace="#LoadModule php5_module libexec\/apache2\/libphp5.so"
```

This worked for me when I copied your example.

---

### Post by Drenriza on 2011-12-14
> **lechien73 said:**
> Ah yes, forgot to mention - also enclose your variable declaration in double quotes, and escape the forward slashes so:

```
replace="#LoadModule php5_module libexec\/apache2\/libphp5.so"
```

This worked for me when I copied your example.

Thanks. Now it's working :p

---

