---
title: "How to install EZ Intranet Messenger on Ubuntu"
date: 2011-05-29
forum: General Help
---

### Post by Elentir on 2011-05-29
I'm trying to install EZ Intranet messenger on Ubuntu 8.10. I already figured out I need Java installed so I did the following:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

I downloaded the zip from the site and proceeded with the following code given on the EZIM site:

```
$ java -jar PATH_TO_EZIM.JAR &
```

But then I get the following 'error':

```
toolbox@toolbox-desktop:~$ $ java -jar PATH_TO_EZIM.JAR &
[1] 5563
toolbox@toolbox-desktop:~$ bash: $: command not found

[1]+  Exit 127                $ java -jar PATH_TO_EZIM.JAR

```

Any ideas?

---

