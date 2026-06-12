---
title: "Linux charset GUI?"
date: 2011-09-04
forum: General Help
---

### Post by qwertyjjj on 2011-09-04
Is there a LINUX GUI program that can show you which characters are incorrect?
I keep trying to save my file as ISO with French characters and gedit errors.

It does not like these characters in ISO:
&#65279;Avec ses prix compétitifs et ses forfaits flexibles, Proxyxxxxxx vous offre l'accès à un serveur PROXY et/ou RÉSEAU PRIVÉ VIRTUEL (VPN) géolocalisé en France, qui vous permettra d’accéder à l’internet sans restrictions de partout dans le monde et ce, pour une grande variété d'utilisat

---

### Post by Paddy Landau on 2011-09-04
Any character is legal in Linux, apart from the forward slash ('/') because it is a directory separator.

However, I advise you stick to simple characters for ease of use and especially if you want it portable between different operating systems.

EDIT: I am presuming you mean a file name?

---

### Post by qwertyjjj on 2011-09-04
> **Paddy Landau said:**
> Any character is legal in Linux, apart from the forward slash ('/') because it is a directory separator.

However, I advise you stick to simple characters for ease of use and especially if you want it portable between different operating systems.

EDIT: I am presuming you mean a file name?

No, a character set like ISO8859-1 or UTF-8.
The text above has French characters.
I need to save it in IS)8859-1 for it to work on the webpage and gedit won;t save it as it says there are illegal characters.

---

### Post by tredegar on 2011-09-04
UTF-8 encoding should work across all platforms. It copes with French characters (and Thai, Bengali, Arabic, you-name-it). Linux has used it for *years*.

Converting UTF-8 to ISO-xxxx is a backwards step.

If your web page has problems, then maybe there is something wrong with your server, or the browser you are using to access it?

---

### Post by ofnuts on 2011-09-04
> **qwertyjjj said:**
> Is there a LINUX GUI program that can show you which characters are incorrect?
I keep trying to save my file as ISO with French characters and gedit errors.

It does not like these characters in ISO:
&#65279;Avec ses prix compétitifs et ses forfaits flexibles, Proxyxxxxxx vous offre l'accès à un serveur PROXY et/ou RÉSEAU PRIVÉ VIRTUEL (VPN) géolocalisé en France, qui vous permettra d&#8217;accéder à l&#8217;internet sans restrictions de partout dans le monde et ce, pour une grande variété d'utilisat
There is no such thing as "ISO". For French, there are ISO-8859-1 (old style)  and ISO-8859-15 (new style, with Euro symbol).

Your problem are invalid apostrophes: "qui vous permettra d?accéder à l?internet". These are opening (or closing?) slanted apostrophes[SIZE=4] (**&#8217;**)[/SIZE], while ISO-8859-15 only knows about the plain "straight" one[SIZE=4] (**'**)[/SIZE]. It's quite easy to spot... copy/paste contents to new file, save your original file as 8859-15, ignoring any warnings, close, reopen, and compare with copy/pasted version. Any changed characters aren't supported by 8859-15.

---

### Post by qwertyjjj on 2011-09-04
> **ofnuts said:**
> There is no such thing as "ISO". For French, there are ISO-8859-1 (old style)  and ISO-8859-15 (new style, with Euro symbol).

Your problem are invalid apostrophes: "qui vous permettra d?accéder à l?internet". These are opening (or closing?) slanted apostrophes[SIZE=4] (**’**)[/SIZE], while ISO-8859-15 only knows about the plain "straight" one[SIZE=4] (**'**)[/SIZE]. It's quite easy to spot... copy/paste contents to new file, save your original file as 8859-15, ignoring any warnings, close, reopen, and compare with copy/pasted version. Any changed characters aren't supported by 8859-15.

I thought it was that but I tried replacing them and it didn;t seem to make a difference. Is there a charset that I need my keyboard on because as far as I am aware there is only one type of apostrophe.

---

### Post by qwertyjjj on 2011-09-04
I just pasted this exact text after replacing all the apostrophes and it errors again:

```

&#65279;Avec ses prix compétitifs et ses forfaits flexibles, Proxyxxxxxx vous offre l\'accès à un serveur PROXY et/ou RÉSEAU PRIVÉ VIRTUEL \(VPN\) géolocalisé en France, qui vous permettra d\'accéder à l\'internet sans restrictions de partout dans le monde et ce, pour une grande variété d\'utilisations.

```

The database is UTF8-general-ci, but when I code the page in UTF8, it just shows bizarre symbols instead of accents.

---

### Post by qwertyjjj on 2011-09-04
> **tredegar said:**
> UTF-8 encoding should work across all platforms. It copes with French characters (and Thai, Bengali, Arabic, you-name-it). Linux has used it for *years*.

Converting UTF-8 to ISO-xxxx is a backwards step.

If your web page has problems, then maybe there is something wrong with your server, or the browser you are using to access it?

The database is UTF8-general-ci, but when I code the page in UTF8, it just shows bizarre symbols instead of accents.
```

ï»¿Avec ses prix compÃ©titifs et ses forfaits flexibles, Proxyxxxxxx vous offre l'accÃ¨s Ã  un serveur PROXY et/ou RÃ&#8240;SEAU PRIVÃ&#8240; VIRTUEL \(VPN\) gÃ©olocalisÃ© en France, qui vous permettra d'accÃ©der Ã  l'internet sans restrictions de partout dans le monde et ce, pour une grande variÃ©tÃ© d'utilisations. 

```

---

### Post by tredegar on 2011-09-04
Sorry that you are having these problems with language-characters.

Linux all works fine for me, across all languages and encoding, with UTF-8 (as the default, it seems).

But I wonder if you are using / have used windows (MSoft) applications somewhere to edit your pages? I don't think MSoft are quite as much UTF-8 aware as linux is (but my version of win is '98). The last time I visited MS I had to do "codepages" or something. It has been quite some time since I had to do that as I use linux 100% now.

Also:
> The database is UTF8-general-ci

I do remember that when I played with MySQL there was an option to choose the database encoding, fairly early on in the setup. I did not really understand it at the time, and soon lost interest anyway (my interest does not lie with databases, or encoding), but maybe you made the wrong choice when you set the database up?

Why did you choose **UTF8-general-ci** over just **UTF-8**?

I realise that this does not answer your question, but it might help you search for a solution.

Best wishes.

---

### Post by ofnuts on 2011-09-04
> **qwertyjjj said:**
> I thought it was that but I tried replacing them and it didn;t seem to make a difference. Is there a charset that I need my keyboard on because as far as I am aware there is only one type of apostrophe.Your keyboard is fine. Actually there are other apostrophes in that line that are OK. The only explanation that comes to mind is that you pasted that part of text from somewhere else.

---

### Post by ofnuts on 2011-09-04
> **qwertyjjj said:**
> The database is UTF8-general-ci, but when I code the page in UTF8, it just shows bizarre symbols instead of accents.
```

ï»¿Avec ses prix compÃ©titifs et ses forfaits flexibles, Proxyxxxxxx vous offre l'accÃ¨s Ã  un serveur PROXY et/ou RÃ&#8240;SEAU PRIVÃ&#8240; VIRTUEL \(VPN\) gÃ©olocalisÃ© en France, qui vous permettra d'accÃ©der Ã  l'internet sans restrictions de partout dans le monde et ce, pour une grande variÃ©tÃ© d'utilisations. 

```Yes, this is an UTF-8 byte stream interpreted as ISO-8859. If you code the page in UTF-8, you have to make sure the encoding in the <meta> tags is correct:
```
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```or that the HTTP headers  returned by your server say:
```
Content-Type: text/html; charset=utf-8
```They are exactly the same thing, the <meta> was invented when one couldn't trust the server to produce the Content-type header. Not sure which one gets the last word when they are both present and differ. Might be browser-dependent...

---

### Post by qwertyjjj on 2011-09-05
I get this.
So, somewhere in my code, I need to change it to fr and utf?

```

<!doctype html public "-//W3C//DTD HTML 4.01 Transitional//EN">
<html dir="LTR" lang="en">
<head>
 <title>Proxyxxxxxx - serveur proxy France</title>
 <meta name="Description" content="Proxyxxxxxx - serveur proxy France" >
 <meta name="Keywords" content="Proxyxxxxxx - serveur proxy France" >
 <meta name="googlebot" content="all" >
 <meta name="robots" content="noodp" >
 <meta name="slurp" content="noydir" >
 <link rel="canonical" href="http://www.Proxyxxxxxx.fr/cart/index.php?osCsid=a65aca5c585dbf1a0eb4e2bd8af9bf02" >

 <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" >


```

---

### Post by ofnuts on 2011-09-05
> **qwertyjjj said:**
> I get this.
So, somewhere in my code, I need to change it to fr and utf?

```

<!doctype html public "-//W3C//DTD HTML 4.01 Transitional//EN">
<html dir="LTR" lang="en">
<head>
 <title>Proxyxxxxxx - serveur proxy France</title>
 <meta name="Description" content="Proxyxxxxxx - serveur proxy France" >
 <meta name="Keywords" content="Proxyxxxxxx - serveur proxy France" >
 <meta name="googlebot" content="all" >
 <meta name="robots" content="noodp" >
 <meta name="slurp" content="noydir" >
 <link rel="canonical" href="http://www.Proxyxxxxxx.fr/cart/index.php?osCsid=a65aca5c585dbf1a0eb4e2bd8af9bf02" >

 <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" >


```
UTF-8, definitely if you serve the page encoded as UTF-8.  'fr' is not important (nor is 'LTR'...).

I tend to put the 'content-type' tag as close as possible to the top, because it will often cause a restart of the HTML parsing, so the less the browser does before, the better.

---

### Post by qwertyjjj on 2011-09-05
> **ofnuts said:**
> UTF-8, definitely if you serve the page encoded as UTF-8.  'fr' is not important (nor is 'LTR'...).

I tend to put the 'content-type' tag as close as possible to the top, because it will often cause a restart of the HTML parsing, so the less the browser does before, the better.

This is bizarre because when I copy and pasted the text from gedit to the php page it errored. Yet, on Windows today and posting from Wordpad to the php file, there were no errors.
Why would the program I am copying from make a difference?

---

### Post by ofnuts on 2011-09-05
> **qwertyjjj said:**
> This is bizarre because when I copy and pasted the text from gedit to the php page it errored. Yet, on Windows today and posting from Wordpad to the php file, there were no errors.
Why would the program I am copying from make a difference?One possible explanation is that in Windows the clipboard only contains "wide" chars (IIRC all system calls in modern Windows use wide characters) while on Linux it could be a byte stream interpreted differently between writer and reader. But this is a shot in the dark, I haven't dealt with clipboard APIs in a very long time.

---

