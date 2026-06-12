---
title: "Running java in background with &amp;"
date: 2011-02-16
forum: General Help
---

### Post by willroberts on 2011-02-16
Hello all,

I am running Ubuntu 10.10, and I am trying to run a java process in the background of a terminal, so I can continue to use that terminal.

Other applications will run in the background just fine, but when I run my java application, I cannot change the status of the process from "Stopped" after suspending it.

Here is my command syntax, along with some commands I have tried and their outputs:

[COLOR="Blue"]$ java -jar application.jar nogui &
[2] 985
$ jobs
[2]+ Stopped     java -jar application.jar nogui
$ bg %2
[2]+ java -jar application.jar nogui
$ bg
[2]+ java -jar application.jar nogui
$ jobs
[2]+ Stopped     java -jar application.jar nogui[/COLOR]

There were [1]- entries, but I removed them for simplicity.

Any help will be greatly appreciated! :)

---

### Post by b0b138 on 2011-02-16
I had to make a script for one I use

```
#!/bin/sh
cd ~/path
java -jar application.jar
```

then you can ```
./javaapp.sh &
```

or create a launcher to it

---

### Post by willroberts on 2011-02-16
Thanks for the info. I've created application.sh, and run it with ./application.sh &, but the process is still stopped. When I pull the process to the foreground with fg, it starts to run normally. Running application.sh without & works normally as well.

I'm not sure why this won't run in the background with my other programs. :/

---

### Post by willroberts on 2011-02-17
Someone at the office recommended that I try the 'screen' command. I'll work on this later and post the results.

---

### Post by willroberts on 2011-02-17
screen works perfectly. I installed it with 'sudo aptitude install screen', which downloaded and installed three required packages, and then after a quick look at 'man screen', I was up and running. Here's my process:

$ screen java -jar application.jar nogui [start java application]
Ctrl+a+c [open new screen]
Ctrl+0 [recall screen 0, the java application]

That's it! :)

---

