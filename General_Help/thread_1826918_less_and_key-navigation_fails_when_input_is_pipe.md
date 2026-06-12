---
title: "less and key-navigation fails when input is pipe"
date: 2011-08-17
forum: General Help
---

### Post by danielsbrewer on 2011-08-17
I am finding that keyboard arrows are failing to navigate when the input is piped to it.  For example:
```
php script.php | less
```
when the arrow keys are pressed you get ^[OB or ^[OA.  When you pipe to log file and then use less on that the arrow keys work fine
```
php script.php > temp.txt
less temp.txt
```

Any ideas how I can overcome this?  This us using Ubuntu 10.04 LTS and from an SSH session coming in from a mac.  I tried SSHing into another server and this problem was not present.  There is no difference in .inputrc file.

---

### Post by Tolaris on 2012-04-16
I have the same, very irritating problem. However, it seems specifically tied to output from the PHP binary, which sets the terminal to line mode before the pipe. See:

[http://stackoverflow.com/questions/5238522/how-do-i-get-less-or-more-to-recognize-keystrokes-when-piping-from-a-cli-php-scr](http://stackoverflow.com/questions/5238522/how-do-i-get-less-or-more-to-recognize-keystrokes-when-piping-from-a-cli-php-scr)

---

