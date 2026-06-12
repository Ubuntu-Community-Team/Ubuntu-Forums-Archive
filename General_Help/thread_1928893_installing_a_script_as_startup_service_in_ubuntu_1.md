---
title: "installing a script as startup service in ubuntu 10.10"
date: 2012-02-20
forum: General Help
---

### Post by JibinJohn on 2012-02-20
I have a script `openerp-server.py` in `~/openerp/stable6/server/bin/`.I want it to be run at startup.(As a service or not - I don't know the difference)

These are the steps I followed

1 Created a script 'openerp-server' with the following lines in `/etc/init.d/`

    #!/bin/sh
    cd ~/openerp/stable6/server/bin/
    exec /usr/bin/python ./openerp-server.py $@

2 Made the script executable by using the following command

    sudo chmod +x /etc/init.d/openerp-server

3 Made the link run on startup by using the following command
    
    sudo update-rc.d openerp-server 

I checked using sysv-rc-conf.And openerp-server was selected for run level 2,3,4,5. 

Now after restarting I checked if the `openerp-server.py` is running, it was not running.

Please help.

---

### Post by Paddy Landau on 2012-02-21
Must it run when the computer is started or when you log in? The answer will be different.

To start when you log in, simply add it to Startup Applications.

To start when the computer starts up, try adding it to the file /etc/rc.local. Note that it must end with exit 0, so place your command before that line.

---

### Post by cortman on 2012-02-21
> **Paddy Landau said:**
> To start when you log in, simply add it to Startup Applications.


+1. I messed around with init, crontab, rc.local, you name it for a long time trying to get a simple script to run at startup. Not sure what I was doing wrong, but simply adding it to Startup Applications (in System Settings) made it work.

---

### Post by Paddy Landau on 2012-02-22
> **cortman said:**
> +1. I messed around with init, crontab, rc.local, you name it for a long time trying to get a simple script to run at startup. Not sure what I was doing wrong, but simply adding it to Startup Applications (in System Settings) made it work.
Usually -- though unfortunately not always -- there is an easy way to do something.

---

