---
title: "Run ASP Locally"
date: 2012-03-13
forum: General Help
---

### Post by Remado on 2012-03-13
I have tried installing many things, but without success. Going to [http://127.0.0.1/~user/]("http://127.0.0.1/%7Euser/") results in a list of the contents of /home/user/public_html, which is good. When I click my test.asp file, it only displays the contents of the file.```
<html>
<body>
<% response.write("Hello, world!") %>
</body>
</html>
```After following various guides and having no luck, it almost seems impossible on my own. Can anyone give me a simple guide to getting this set up? It would be deeply appreciated.

By the way, I prefer PHP, but I need to install ASP stuff so I can help develop for a website that is powered by ASP and the owner doesn't want to migrate to PHP. Thank you.

---

### Post by Cheesemill on 2012-03-13
ASP is a Microsoft server technology which doesn't run natively on Linux.

There is a program called Mono which is an open source project which will let you run certain ASP files on apache server using the mod_mono extension but not all ASP features have been implemented (and probably never will be).

Take a look at the Mono website for more details but I wouldn't ever use it on a production system.

For serving Microsoft ASP websites you really need to use Microsoft IIS as your web server.

[http://www.mono-project.com/Mod_mono](http://www.mono-project.com/Mod_mono)
[https://help.ubuntu.com/community/ModMono](https://help.ubuntu.com/community/ModMono)

---

### Post by directhex on 2012-03-13
ASP is a long-dead technology from 1998-2002. There are some commercial implementations of the spec, as listed on [http://en.wikipedia.org/wiki/Active_Server_Pages#Alternative_implementations](http://en.wikipedia.org/wiki/Active_Server_Pages#Alternative_implementations) - but assume they won't work.

Mono can only do ASP.NET, which is the successor to ASP - the only thing they really have in common is the name

Mono will NOT help you run ASP, only ASP.NET.

---

### Post by squilookle on 2012-03-13
I know the feeling. I have some servers at work that have ASP applications that I have to maintain. 

As others have said, IIS is the best bet if you can get your hands on a system that runs it. I believe there are ways of running ASP scripts on a LAMP server, but that they are not worth the effort/trouble - and even if you get them running, your scripts might not work as expected with the MS server in the end. 

If you don't have/can't get access an MS server, does the owner of the website perhaps have a development environment that you can use?

---

### Post by mbm1234 on 2012-03-13
Hello, if you have a Window computer you can download Microsoft Web Matix (it's free) tool development.

[http://www.asp.net/web-pages](http://www.asp.net/web-pages)

[http://www.microsoft.com/web/webmatrix/features.aspx](http://www.microsoft.com/web/webmatrix/features.aspx)

---

