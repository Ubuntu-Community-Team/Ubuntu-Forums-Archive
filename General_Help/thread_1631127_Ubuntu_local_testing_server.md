---
title: "Ubuntu local testing server"
date: 2010-11-26
forum: General Help
---

### Post by nVee on 2010-11-26
Hi guys,

I have been apointed to setup a local testing webserver for our company. Due to most of us not being too server savvy, we installed Desktop 10.10 because it gives us the flexibility of having a GUI and also having access to terminal. Please, I really dont want comments like "why dont you install server version ect" as I think the above point explains the scenario and from my experience we dont need it for our requirements.

Our requirements:
1) Apache/PHP/MySQL/PHPMyAdmin
2) Having the Zend Framework pre-installed within the structure it would greatly help, but this really is optional.
3) version control :)

What I have done so far:
1) Installed Ubuntu and did the network setup
2) I turned or remote support
3) installed a basic lamp server using sudo tasksel install lamp-server
4) Installed fine and set the default mysql password to blank (yes I understand the security risk but as I mentioned this is really just for local server enviroment and not for production purposes.
5) going to either [http://192.168.0.211](http://192.168.0.211) or [http://webserver.local](http://webserver.local) returns the "It works" page on both the server and any machine on our network.


My question:
1) Where is htdocs folder located and how do I set ubuntu up so that the other users on the network can access the folder, upload files ect? I read some article somewhere that users may have to FTP files to the temp server which to me defeats the point, so is there a way for me to upload it directly over the network. we generally dont mind working on something like [http://webserver.local/livesites/sitename](http://webserver.local/livesites/sitename) as appose to creating seperate apache entries for different sites.
2) How do I install PHPmyAdmin specifically considering that I installed the lamp-server. There is an array of results online on how to install it, but I am getting more errors than anything else, especially with packages not available, resources being used ect?
3) Would you advise/recommend that we rather install a complete server setup like the zend server CE to cover all of our needs and if so, can you advise me how do I a) install that and b) uninstall the existing setup?
4) Can you advise me on a good resource to install version control for any enviroment I end up using?
5) I tried to activate the remote desktop so that I can access the server from my laptop but without any success. Everything appears setup, but going to Remote Desktop on Windows 7 e.g. and entering either the PC name (webserver.local) or the IP 192.168.0.211 (the server IP) says I cannot connect because the remote server might be off blah blah. I can ping the server from my win machine, and tried the same from another windows machine without success. Unfortunately we're not presented with a real troubleshooting answer, so I hope someone can help me by giving me a list of possible problems or things to look at?

As a extra note, we use both Mac's and PC's on the network.

Thank you in advance for any help, I greatly appreciate it!

---

