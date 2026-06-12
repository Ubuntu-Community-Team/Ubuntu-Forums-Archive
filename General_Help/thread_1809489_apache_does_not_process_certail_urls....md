---
title: "apache does not process certail urls..."
date: 2011-07-21
forum: General Help
---

### Post by mikejonesey on 2011-07-21
urls like;

[http://.../webcgi/webplus.exe?about](http://.../webcgi/webplus.exe?about)

or

[http://.../cgi-914/pollit/Poll_It_SSI_v2.0.cgi?data_dir=\etc\passwd%00](http://.../cgi-914/pollit/Poll_It_SSI_v2.0.cgi?data_dir=\etc\passwd%00)

apache won't process so i can't display a 404 page... any ideas?

request does reach server, don't think reaches apache though...

---

### Post by mikejonesey on 2011-07-21
this is so wierd...

[http://www.mikejonesey.co.uk/webcgi/webplus.exe?about](http://www.mikejonesey.co.uk/webcgi/webplus.exe?about)
timesout

[http://www.mikejonesey.co.uk/webcgi/webplus.exe?abou](http://www.mikejonesey.co.uk/webcgi/webplus.exe?abou)
goes to 404

[http://www.mikejonesey.co.uk/webcgi/webplu.exe?about](http://www.mikejonesey.co.uk/webcgi/webplu.exe?about)
goes to 404

[http://www.mikejonesey.co.uk/webcg/webplus.exe?about](http://www.mikejonesey.co.uk/webcg/webplus.exe?about)
goes to 404

???

---

### Post by WorMzy on 2011-07-21
Well, firstly, "http://.../webcgi/webplus.exe?about" won't work, unless you've got "..." in your hosts file; and I don't think that's an acceptable hostname in any case.

Secondly, what is "webplus.exe", and what are you expecting apache to do with it?

---

### Post by mikejonesey on 2011-07-22
lol ... was a suppressed domain example, see second post for full urls, webplus.exe is a non exisitant file, the url should resolve to my 404 error page

---

### Post by WorMzy on 2011-07-22
I see. Okay, what does access.log and error.log have to say on the matter? Is there anything in your config that could be causing an endless loop? e.g. Do you have any rewrite rules?

---

### Post by SeijiSensei on 2011-07-22
If you want Apache to run executables, you need to read this first: 
[http://httpd.apache.org/docs/current/howto/cgi.html](http://httpd.apache.org/docs/current/howto/cgi.html)

---

### Post by mikejonesey on 2011-07-22
thanks for the replys,

@WorMzy
it's not stuck in a mod-rewrite
there is no out put in the logs, i belive the request is maybe no reaching apache, i would expect to at least see an entry in the error log if it were...

@SeijiSensei
i have no intention of running a script, the script does not exist, i wish for it to resolve to a 404...

any more sugestions? i can confirm the request is reaching the server...

---

### Post by mikejonesey on 2011-07-22
bump :)

---

### Post by mikejonesey on 2011-07-22
still noone :(;

is it by coincidence that;

[http://www.godaddy.co.uk/cgi/post16.exe](http://www.godaddy.co.uk/cgi/post16.exe) = 404
[http://www.godaddy.co.uk/cgi/post16.exe|](http://www.godaddy.co.uk/cgi/post16.exe|) = endless loop...

(godaddy is my server provider...), this must be something to do with a network firewall? if it is i must say this is pants networking... I will not stop till i have the answer... never do...

---

### Post by mikejonesey on 2011-07-23
c'mon...

latest tests indicate the server is receiving and processing the url's but for some the client on an outside network is not receiving the reply...

I have come to this conclusion by telneting to apache from;

1. my laptop on an outside network;
```
telnet ...
GET /perl.exe HTTP/1.1
Host ...

> no responce....
```2. from the server...
```
telnet ...
GET /perl.exe HTTP/1.1
Host ...

> 301 > 404 responce...
```so how can i confirm exactly where the packet is being stopped?

ps both requests meet the server... (netstat)...

checking apache logs, perl.exe apears only from the local request, so apache is probably not recieving the request from the remote... where to look next?...

---

