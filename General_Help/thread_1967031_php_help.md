---
title: "php help"
date: 2012-04-27
forum: General Help
---

### Post by piek on 2012-04-27
Hi guys,

I downloaded php5.3 source code here: [http://us3.php.net/get/php-5.3.11.tar.bz2/from/a/mirror](http://us3.php.net/get/php-5.3.11.tar.bz2/from/a/mirror)

The tutorial book I'm reading says:

"to run the "configure" script inside the distribution folder to set various compile-time options. This allows you to specify things such as compiling PHP as an Apache module, and including or excluding specific libraries such as the GD or MySQL library.

Then run make to compile PHP
Then make install to install the compiled binary files."

The entire purpose of this is to compile the PHP myself however I'm having trouble finding "make". Not too sure what that means. Also, when opening the configure file, I see the following code: "#! /bin/sh"

Can someone help me to begin compiling PHP in linux? Thanks!

---

### Post by linuxonbute on 2012-05-08
> **piek said:**
> Hi guys,

I downloaded php5.3 source code here: [http://us3.php.net/get/php-5.3.11.tar.bz2/from/a/mirror](http://us3.php.net/get/php-5.3.11.tar.bz2/from/a/mirror)

The tutorial book I'm reading says:

"to run the "configure" script inside the distribution folder to set various compile-time options. This allows you to specify things such as compiling PHP as an Apache module, and including or excluding specific libraries such as the GD or MySQL library.

Then run make to compile PHP
Then make install to install the compiled binary files."

The entire purpose of this is to compile the PHP myself however I'm having trouble finding "make". Not too sure what that means. Also, when opening the configure file, I see the following code: "#! /bin/sh"

Can someone help me to begin compiling PHP in linux? Thanks!
Start up a terminal program.
When you are in the directory with the configure file in it type the following and press the Enter key:
```

./configure

```this will run the configure script.
When it has finished  type the following and press the Enter key:
```

make

```Then type the following and press the Enter key:
```

sudo make install

```It will ask for you password which you will need to supply.

That should be it all done

---

