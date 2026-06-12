---
title: "Recommended light ubuntu applications"
date: 2012-02-02
forum: General Help
---

### Post by LuniTux on 2012-02-02
Hello,

I am building an ubuntu 10.04 server. I have installed a minimal gui on it with a startup script.

```
sudo apt-get install xinit blackbox bbkeys numlockx conky slim
```

and my .xsession file

```
numlockx on &
bbkeys &
conky &
exec blackbox
```

This computer is being used for web, ftp,  and data hosting.

What other lightweight programs would be good for me to install that are not necessities to run the server (apache, mysql, php, vsftp, etc.)

Thanks,



----------
Apps

openssh-server
wicd-curses

---

### Post by Rodney9 on 2012-02-02
What do you wont to do ? What sort of programs, terminal, text writer, what ?

Rodney

---

### Post by Rodney9 on 2012-02-02
Double Post

---

### Post by Tamlynmac on 2012-02-02
Might I suggest you use a format similar to [this]("https://wiki.ubuntu.com/Lubuntu/Applications") for defining which apps are required (based on your impose demands).

Then request feedback on your predefined objectives. You could provide members with a listing of what you believe are critical apps and ask for any futher recommends. An open ended question may only result in recommendations that are unnecessary or don't meet with your expectations.

Narrowing down your requirements and exposing your objectives may have a more positive impact on your project. Perhaps, the use of a spreadsheet to list your pre-existing apps would assist other members in understanding said objectives and providing beneficial feedback.

Just a thought. Good Luck.

---

### Post by snowpine on 2012-02-02
I recommend using your favorite system monitor (for example 'top' or conky can be used to display this information) to analyze your performance issues (which you haven't clearly articulated to us).

For example if your CPU is running at 100% it may require a different solution than if your RAM is at 100%.

---

### Post by LuniTux on 2012-02-03
Any changes made to files,data,etc. will be made from another computer.

current programs:
text editor: nano
   terminal: xterm
sys monitor: conky (config from [http://crunchbanglinux.org/.../my-conky-config/]("http://crunchbanglinux.org/forums/topic/59/my-conky-config/")) (2nd post with minor changes)
   firewall: ufw
 send email: ssmtp/mutt
battery mon: apcupsd

web browser: (should not need)

---

I guess what I should be asking is what programs should I use to make the server more secure/ easier to use? (opening/closing ports, knowing when someone is connected to the server, list connection times from external computers, etc.)

---

