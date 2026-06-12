---
title: "Delaying Startup of Automatically Started Programs"
date: 2010-05-16
forum: General Help
---

### Post by gwm on 2010-05-16
Recently I have had a run of random errors on boot up. Finally, the quit button, top right of the screen disappeared permanently.

I am convinced it is because I added Evolution to the programs that start automatically when I login to Ubuntu (auto login). Evolution uses the Internet connection which hasn't been successfully established by the time it starts. In the past, this would crash Ubuntu. It seemed to be fixed by this stage, but maybe not.

Is there some way of delaying the startup of a program in the automatic startup list - to give the rest of everything time to settle in - before it starts trying to use other startup resources?

---

### Post by labinnsw on 2010-05-18
Save this as .evolutionstart.sh in your home directory. Be sure to make it executable

```
#!/bin/bash
sleep 10
killall evolution &
sleep 15
evolution
```

Then substitute this for the  evolution command in your startup applications.
```
/home/username/.evolutionstart.sh
```

Adjust the times until you get it right.

---

### Post by mike555 on 2010-05-18
to delay the startup of an app in the startup , use a command like ;
      
 by adding    bash -c "sleep 20:         to the command it sleeps for 20 seconds before starting . notice the spaces , and quotes (before sleep and after the command )  ....

     bash -c "sleep 20; /usr/bin/checkgmail"     for instance for checkgmail ......
   ==== put this Checkgmail text in the startup programs edit ====


  or ;

 putting   bash -c "sleep 20; /usr/bin/thunderbird     in the startup list will start thunderbird 20 seconds after when you startup ... good to use with Thunderbirds add-on " firebird" , which can minimize Thunderbird to the top toolbar , letting it run and tell you when you have mail ...

---

### Post by gwm on 2010-05-22
Thank you for the responses. I haven't got round to doing it yet, but I know they will work.

I am ashamed to say that even after over 5 years of using Linux, I am still not familiar with **bash** and scripting, even after writing many thousands of lines of script on earlier operating systems. Your answers prompted me to do a lot more reading on the subject and I am now a much happier happy chappie.

Thank you once again.

---

