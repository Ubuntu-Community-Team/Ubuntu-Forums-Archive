---
title: "like windows task manager applcations"
date: 2010-11-12
forum: General Help
---

### Post by zeebrazil on 2010-11-12
Hi Forum ,
                I am very new to ubuntu , through system monitor option i am able to see only the process but not current application as like windows task manger . 
how can i see the running application names. what are the command that i have to use i use ps with all options but no luck.
exactly what i want is 
If i open gmail in firefox then in the windows taskmanger under application tab it shows application name gmail.
i need exactly in ubuntu . i only see the firefox in process list but not gmail as application .
i need it for my programming, please assist me .

                 Thanking you in advance.

---

### Post by sikander3786 on 2010-11-12
> If i open gmail in firefox then in the windows taskmanger under application tab it shows application name gmail.

I haven't seen that for Firefox 3.xx. It might be FF 4 Beta or Google Chrome that run Tabs as a separate processes???

---

### Post by zeebrazil on 2010-11-12
Thanks for your reply
Let me clear , If i open firefox in windows then in the task manger under applications tab , it shows 
Mozila Firefox and show the status running .
Now if i open the gmail in that tab or in separate tab 
the application name changes Mozila Firefox to Gmail:Email from Google-Mozila Firefox

like that i need application names in ubuntu 
i am not taking about process list .
Hope it make clear.

---

### Post by Morbius1 on 2010-11-12
I'm not at a linux machine at the moment but there is an app called System Monitor that does this. It should be in the Menu somewhere.

The package is gnome-system-monitor

---

### Post by 7h3d4rk0n3 on 2010-11-12
I don't think there is anything like that in Linux, as Linux doesn't care about what web page you are on. The process is Firefox either way, same for Windows. No matter what tab you have open the process that is actually running is Firefox.exe. All the applications tab is doing, is showing the user in an easier way what is using the processes. What is it you are trying to program?

---

### Post by zeebrazil on 2010-11-12
Thanks for all replies ,
                    
                                    In windows using my java code i am extracting the application names as i need .
and i set the control if the application name is gmail( For example) , it should perform coded task.
i succeeded in windows .i am able get the application name .
now i start trails in ubuntu . but no luck .

---

### Post by 7h3d4rk0n3 on 2010-11-12
I see. Could you perhaps do something like If appname (firefox) contains "Gmail" do code? I'm not too familiar with Java, but I would assume you would be able to do something like that.

---

### Post by sikander3786 on 2010-11-12
> **zeebrazil said:**
> Thanks for your reply
Let me clear , If i open firefox in windows then in the task manger under applications tab , it shows 
Mozila Firefox and show the status running .
Now if i open the gmail in that tab or in separate tab 
the application name changes Mozila Firefox to Gmail:Email from Google-Mozila Firefox

like that i need application names in ubuntu 
i am not taking about process list .
Hope it make clear.
Thats exactly I was talking about.

I think Chromium browser runs all it tabs independent of each other so that if one of them crashes, it doesn't crash the whole browser. And FF 4 also follows the same path. That way if you open Gmail in one tab, the process name might change to the web page you just opened in any system monitor.

But it doesn't. I have just checked with both Chromium and FF 4 beta, no luck.

As for FF 3.xx, the browser runs as a single process regardless of how many tabs are opened there, therefore system monitor sees only one process i.e, browser itself and doesn't name the web pages open there.

Hope this makes sense :-)

---

### Post by zeebrazil on 2010-11-12
yes ofcourse even in the windows task manger under the process list ,it shows firefox.exe even we open any number of tabs , but under applications tab there it shows the open tab name(application name ex: gmail )  and it status as running.
so through coding i can perform my action like  
if (appname == gmail) {   } [for example]  
Successfully.

but in ubuntu i don't get this appname which was struck me  to move forward.

thanks for your replies and i have to look at for another alternatives.

---

