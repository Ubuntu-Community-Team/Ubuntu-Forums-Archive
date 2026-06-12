---
title: "Can't get captcha to work!"
date: 2010-12-23
forum: General Help
---

### Post by Bluesplayer on 2010-12-23
Hi

I have installed the latest ubuntu server along with a database driven store.  The store uses captcha on the review submission but I can't get it to work.  When I click on the CaptchaSecurityImages.php I get this message:

```
Error in imagettfbbox function
```I have setup a test page with a new download of the captcha script so all paths are definitely ok.  Here is the form link:

[http://81.174.251.67/electronics/tvs/test/form.php](http://81.174.251.67/electronics/tvs/test/form.php)
[URL="http://81.174.251.67/electronics/tvs/test/form.php"]Captcha Form
[/URL]
Trouble is I can't find out anymore information regarding above.

In error log there is this:

```
PHP Warning:  imagettfbbox(): Could not find/open font in /var/www/electronics/tvs/test/CaptchaSecurityImages.php on line 60
```I have tried altering the path to the font.tff file but I can't see how a path issue would occur when all the files are in the same directory:

```
var $font = 'monofont.ttf';
```What the heck is wrong?

By the way the above works on a hosted server I have:

[http://bluesplayer.co.uk/common/captcha/form.php](http://bluesplayer.co.uk/common/captcha/form.php)
[Captcha Form]("http://bluesplayer.co.uk/common/captcha/form.php")

Regards
Bluesplayer

---

### Post by Bluesplayer on 2010-12-23
I fixed this problem.

1. I downloaded the monofont.ttf using wget:

sudo wget url of monofont.ttf

2. Moved the file to usr/share/fonts/truetype directory:

sudo mv /usr/share/fonts/truetype

Seems to work fine now :D.

---

### Post by proggy on 2011-01-10
None of what you said here works , you obviously omitted lots of information so it`s useless to anyone.

---

### Post by Bluesplayer on 2011-01-10
> None of what you said here works , you obviously omitted lots of information so it`s useless to anyone.Don't understand?

I already fixed this problem.  You can read how both on this forum or by loading the original problem page as I added the fix there too:

[http://81.174.251.67/electronics/tvs/test/form.php](http://81.174.251.67/electronics/tvs/test/form.php)

The problem was that the captcha images were failing to load.  I hope they now show for everyone - and not just me locally?

It appears that Ubuntu looks for such images that captcha uses in the /usr/share/fonts/truetype directory.  There seems to be a path issue going on.  I also had to move fonts there for my forum captcha to work too.

---

### Post by proggy on 2011-01-11
I`m getting this error   --2011-01-11 23:18:04--  [http://url/](http://url/)
Resolving url... failed: Name or service not known.
wget: unable to resolve host address `url'
--2011-01-11 23:18:04--  [http://of/](http://of/)
Resolving of... failed: Name or service not known.
wget: unable to resolve host address `of'
after doing this        ~$ sudo wget url of monofont.ttf

---

### Post by proggy on 2011-01-12
Anyone else have any ideas how to solve this i`m using gyachi version 1.2.10 which i think is the latest version?

---

### Post by Bluesplayer on 2011-01-12
I think you are confused with my solution:

> 1. I downloaded the monofont.ttf using wget:

sudo wget url of monofont.ttfThe above means you download whatever captcha image file you are trying to install using sudo like this:

sudo wget 'wherever your captcha tff file is' 

The above without the quotation marks.  Then you move it to the truetype directory:

sudo mv /usr/share/fonts/truetype

---

### Post by proggy on 2011-01-20
I deleted version 1.2.2 and installed v1.2.0 and captcha is back!

---

