---
title: "No such file or directory found"
date: 2012-06-07
forum: General Help
---

### Post by Milaan on 2012-06-07
[img]http://gyazo.com/8ad0856209f8621a893a05fdd83cbe63.png[/img]

If image is not working: [http://gyazo.com/8ad0856209f8621a893a05fdd83cbe63](http://gyazo.com/8ad0856209f8621a893a05fdd83cbe63)

I was on IRC asking around and no one knew what it was.. This is last resort pretty much, so yeah I have no idea what the problem is.

: puke: < lol

---

### Post by WorMzy on 2012-06-07
Can you post the output of the following commands:

```
ll hldsupdatetool.bin
```

```
file hldsupdatetool.bin
```

```
uname -m
```

---

### Post by lisati on 2012-06-07
Is the .bin file marked as executable?

---

### Post by Milaan on 2012-06-07
> **WorMzy said:**
> Can you post the output of the following commands:

```
ll hldsupdatetool.bin
```

```
file hldsupdatetool.bin
```

```
uname -m
```

[img]http://gyazo.com/c5559f17e286b19782a0cc655b024427.png[/img]
[http://gyazo.com/c5559f17e286b19782a0cc655b024427](http://gyazo.com/c5559f17e286b19782a0cc655b024427)

[img]http://gyazo.com/e37db0f8c3c7a93dbc2ec37a70717891.png[/img]
[http://gyazo.com/e37db0f8c3c7a93dbc2ec37a70717891](http://gyazo.com/e37db0f8c3c7a93dbc2ec37a70717891)

[img]http://gyazo.com/414105c8dd75de09cc11cad2515537c4.png[/img]
[http://gyazo.com/414105c8dd75de09cc11cad2515537c4](http://gyazo.com/414105c8dd75de09cc11cad2515537c4)

---

### Post by WorMzy on 2012-06-07
There's your problem, it's a 32-bit binary, and you're using a 64-bit operating system. Check to see if you can get a 64-bit binary from wherever you downloaded the 32-bit one. If not, you'll have to install the 32-bit libraries that the binary requires.

---

### Post by Milaan on 2012-06-07
:oops:
> **WorMzy said:**
> There's your problem, it's a 32-bit binary, and you're using a 64-bit operating system. Check to see if you can get a 64-bit binary from wherever you downloaded the 32-bit one. [COLOR="Red"]If not, you'll have to install the 32-bit libraries that the binary requires.[/COLOR]

Where can I get this? T

---

### Post by WorMzy on 2012-06-07
They should be in the repositories. I don't use Ubuntu, or the binary you're trying to use, so I can't say for sure what you need. A quick google search suggests that installing ia32-libs-multiarch would be a good place to start.

---

### Post by WorMzy on 2012-06-07
Also, I just noticed that the binary was apparently last modified in 2005, are you sure that it is still known to work with up-to-date libraries? You may be fighting a losing battle here..

---

