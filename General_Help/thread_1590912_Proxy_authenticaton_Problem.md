---
title: "Proxy authenticaton Problem"
date: 2010-10-08
forum: General Help
---

### Post by jamil_1 on 2010-10-08
Hi, I am behind a proxy that requires basic authentication. I have set the environment variable HTTP_PROXY and also set the proxy in System-->Preference --> Network Proxy. Most of the applications work fine. But there are Goldendict and minitube that have problems with proxy. My proxy authentication string is Domain\username:password. From wireshark, I have seen that Goldendict sends the authentication details but leaves out the domain i.e., it sends username:password.

Minitube doesn't send my credentials at all if I launch it from the menu, however when I launch it from terminal it sends same credential as the GoldenDict. Also both the applications print in terminal:

QNetworkAccessCache::addEntry: overriding active cache entry 'auth:proxy-http://username@proxyaddress:80#domain'
QNetworkAccessCache::addEntry: overriding active cache entry 'auth:proxy-http://username@proxyaddress:80'
QNetworkAccessCache::addEntry: overriding active cache entry 'auth:proxy-http://proxyaddress:80'
Network error: "Proxy requires authentication" 105 


Both applications are written in QT so perhaps it has some thing to do with how QT handles proxy credentials. But this is just a speculation. 

Is there a way I could track both of the applications i.e., where are they getting proxy authentication credentials from ? I searched a bit and came across lsof but I don't know how to use it. I have been using Ubuntu for sometime now but still I don't know nothing about internals of linux in general. I think this can be a good learning exercise to track how an application works and what data/process/files it uses. Any suggestion/comment/help are welcome :)

---

