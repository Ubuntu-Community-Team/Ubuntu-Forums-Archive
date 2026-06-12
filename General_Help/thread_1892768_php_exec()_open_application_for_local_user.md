---
title: "php exec() open application for local user"
date: 2011-12-08
forum: General Help
---

### Post by m3bik on 2011-12-08
I'm working on a light use/kiosk system. I have apache2 and php5 installed on Ubuntu 10.04 and I have the browser open the localhost web page by default. I would like to include a link on this page to open oowriter (open office writer) for the end user on the machine.

I've tried

```
exec('oowriter');
```

with no luck. I've also tried setting the DISPLAY value before the command like

```
exec('DISPLAY=:0 oowriter');
```

with no success. I don't mind have the www-data user in the sudoers file if I have to sudo the command or something, but is this possible to do?? I'm not having any luck at all!

It was suggested that I make the www-data user part of the video group, but that didn't work. Also, I can run "php ./myfile.php" in a shell prompt that does open the program specified. It's just when I view the file in a browser that it does not work.

---

### Post by m3bik on 2011-12-09
Well I can get it working with the following code:

```
putenv('DISPLAY=:0');
exec('sudo oowriter');
```

but I do not want to open it with sudo- for obvious security reasons! Is there a group that I can move the www-data user to that will allow it open on the specified display for the end user account?

---

