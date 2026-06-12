---
title: "Why cant I access a file on my server?"
date: 2012-09-25
forum: General Help
---

### Post by SoullessFish on 2012-09-25
I am working on creating a server for minecraft. I have the latest ubuntu server OS all installed and ready. Using Cyberduck i sent the minecraft_server.jar file to my server. but when trying to start the server using "java -Xmx1024m -Xms1024m -jar minecraft_server.jar nogui" it tells me that it is unable to access the file. Is there something I'm missing here? I'm actually not quite sure where on my server Cyberduck sent the file.

thanks.

---

### Post by papibe on 2012-09-25
Hi SoullessFish.

I can't help you with Cyberduck, but it is very easy to download the software using 'wget' on the command line.

Right click on the link, then select 'Copy Link Location', and then in your terminal (connected to your server), paste the link on the terminal:
```
wget link
```

At the momment at this writing this is the actual link:
```
wget https://s3.amazonaws.com/MinecraftDownload/launcher/minecraft_server.jar
```

Let us know how it goes.
Regards.

---

### Post by SoullessFish on 2012-09-25
That worked perfectly papibe. Thank you so much!

---

