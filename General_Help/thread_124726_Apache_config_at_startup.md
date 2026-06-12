---
title: "Apache config at startup?"
date: 2006-02-02
forum: General Help
---

### Post by asterisky on 2006-02-02
Hi,

Newbie to Linux and Ubuntu (yesterday) so go easy on the flames if this is a stupid question.

Trying to host SugarCRM from an Ubuntu box and need to change the Apache http port to 80, Sugar has a bug which stops mail working on any other port. I've changed httpd.conf to contain 'port 80' and I can start Apache manually from a terminal using sudo and that works fine.

Question is, how can I automate the Apache start command so I don't have to give sudo my password manually at each startup? I've entered the line under System/Preferences/Sessions and it just gets ignored. I still have to do a manual start. Is there a way to pass the password to sudo with the command or do I need to put it somewhere else?

AJ

---

### Post by hw-tph on 2006-02-02
Apache listens to TCP/80 by default so you shouldn't have to change anything in the configuration for that.

You can make Apache start automatically by typing **sudo update-rc.d apache2 defaults** if you're using Apache 2 - just omit the "2" if you're using Apache 1.x.



Håkan

---

