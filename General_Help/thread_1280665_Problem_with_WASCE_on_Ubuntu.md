---
title: "Problem with WASCE on Ubuntu"
date: 2009-10-02
forum: General Help
---

### Post by oakdeveloper on 2009-10-02
Hi,

I am having problems starting the WebSphere Application Server Community Edition on my Eclipse IDE in Ubuntu. I have installed WASCE on the default path /opt/IBM/ and also the server adapter on Eclipse. I have got Tomcat server too in the /opt directory. The ownership for the /opt directory is root and with my id I have only read and execute permissions on that directory. When I start Tomcat on Eclipse, it starts up smoothly whereas when WASCE is unable to start and spews exceptions. The cause for the exceptions are that it is not having write permissions on the server directory, i.e., under /opt/IBM/. What should I do to solve this problem? Should I install WASCE on my home directory ? I also want to know why Tomcat doesn't throw any errors when starting up while WASCE does, since both tomcat and WASCE are installed in /opt where write permission is unavailable. Please guide me...

Thanks,
Babu

---

### Post by lingoosoft on 2009-11-24
I think you should install WASCE on your home directory better.

---

