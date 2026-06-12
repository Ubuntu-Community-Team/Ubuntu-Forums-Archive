---
title: "A problem with mozilla based browsers"
date: 2009-12-14
forum: General Help
---

### Post by HamishPillay on 2009-12-14
I installed Ubuntu 9.10. Very happy with it. The only problem is that I cannot use firefox or any mozilla based browser. Opera work, it is rather slow and doesnt load my online banking. 

It is obvious that there is something wrong with the distro. Firefox can browse a website cannot load gmail, wordpress, twitter, FNB. All of these are login sites. is there something that I can change in the software settings or makeup that will allow Firewfox to work. Not even Google Chrome's linux browser works. The only one which allows me to us my email opera but it is limited.

---

### Post by mikewhatever on 2009-12-14
Can you explain what happens exactly and what you mean by 'I can not use firefox ...'. Does Firefox load? Do you get error messages? Does Firefox load websites? If not, what happens? Do you have login errors in Firefox? In short, be more specific, and don't use general terms like, 'something is wrong' or 'can't load'.

---

### Post by jocko on 2009-12-14
> **HamishPillay said:**
> I installed Ubuntu 9.10. Very happy with it. The only problem is that I cannot use firefox or any mozilla based browser. Opera work, it is rather slow and doesnt load my online banking. 

It is obvious that there is something wrong with the distro. Firefox can browse a website cannot load gmail, wordpress, twitter, FNB. All of these are login sites. is there something that I can change in the software settings or makeup that will allow Firewfox to work. [COLOR=Red]Not even Google Chrome's linux browser works.[/COLOR] The only one which allows me to us my email opera but it is limited.
So the problem is *not* limited to mozilla based browsers. Probably some security setting you have enabled in firefox before you installed chromium, and then you imported the settings from firefox when you installed chromium.
Either check your firefox settings or generate a new mozilla profile (rename your ~/.mozilla folder and restart firefox).

---

### Post by running_rabbit07 on 2009-12-14
Run ```
firefox
``` in terminal and paste the outcome here.

---

### Post by HamishPillay on 2009-12-14
With firefox installed I can browse almost any site. I can download apps as well. But it doesnt load Gmail. It doesnt allow me to log into facebook, wordpress or my online bank at [www.fnb.co.za](www.fnb.co.za). It says connecting for a long time but eventually says the page is not available. The guy I bought the disk from says its the hardware, but I was running Kubuntu 9.04 and firefox worked perfectly. I have downloaded various browsers since then and they all have the same problem. I can browse and download, but I cant log into any site requiring a log in. The page that comes up is that the page I am looking for is down. 

the error reads below:

Firefox can't establish a connection to the server at [www.google.com](www.google.com).     


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

Do you know where I should be checking?

---

### Post by lovinglinux on 2009-12-14
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by HamishPillay on 2009-12-14
The Solution:

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). If the settings reset after restart, then delete the file user.js from the profile folder, to reset proxy settings.

Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.

1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle.
4. Restart your Mozilla application and try again.

Yeah that was it. Unbelievable. Thank you very much. I finally feel like my ubuntu is whole again.

merci.

---

### Post by lovinglinux on 2009-12-14
> **HamishPillay said:**
> The Solution:

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). If the settings reset after restart, then delete the file user.js from the profile folder, to reset proxy settings.

Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.

1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle.
4. Restart your Mozilla application and try again.

Yeah that was it. Unbelievable. Thank you very much. I finally feel like my ubuntu is whole again.

merci.

You are welcome.

---

