---
title: "can anyone show me how to install this?"
date: 2012-01-27
forum: General Help
---

### Post by rajohns08 on 2012-01-27
[http://sirupsen.com/a-simple-imgur-bash-screenshot-utility/](http://sirupsen.com/a-simple-imgur-bash-screenshot-utility/)

heads up im a linux newb. i have all the dependencies. when i run: 
```
curl http://sirupsen.com/static/misc/shoot > ~/bin/shoot && chmod 755 ~/bin/shoot
```

i get this output:

% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1260  100  1260    0     0   1764      0 --:--:-- --:--:-- --:--:--  1889

when i type "shoot" it says command not found.

---

### Post by jefelex on 2012-01-27
> **rajohns08 said:**
> [http://sirupsen.com/a-simple-imgur-bash-screenshot-utility/](http://sirupsen.com/a-simple-imgur-bash-screenshot-utility/)

heads up im a linux newb. i have all the dependencies. when i run: 
```
curl http://sirupsen.com/static/misc/shoot > ~/bin/shoot && chmod 755 ~/bin/shoot
```

i get this output:

% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1260  100  1260    0     0   1764      0 --:--:-- --:--:-- --:--:--  1889

when i type "shoot" it says command not found.

do you have a /bin directory in your home folder?  if you do, like it looks, then you should type "./shoot" when in the ~/bin directory to execute the command, since ~/bin is probably not in your executable path

john

---

### Post by rajohns08 on 2012-01-27
> **jefelex said:**
> do you have a /bin directory in your home folder?  if you do, like it looks, then you should type "./shoot" when in the ~/bin directory to execute the command, since ~/bin is probably not in your executable path

john

ok cool it is working now. how do i make an icon out of this script so i can just click the icon when i want it to run?

---

### Post by rajohns08 on 2012-01-27
nvm got it. just made a script file with a command going to bin directory where shoot was located then running it. my icon command was just to location of my script. thanks again

---

### Post by jefelex on 2012-01-28
> **rajohns08 said:**
> nvm got it. just made a script file with a command going to bin directory where shoot was located then running it. my icon command was just to location of my script. thanks again

Your welcome :-)

---

### Post by rajohns08 on 2012-02-25
or you can just make a new icon launcher with the command being:

```
/home/nameofuser/bin/shoot
```

---

