---
title: "browser.fixup.alternate.enabled"
date: 2011-03-09
forum: General Help
---

### Post by SlugSlug on 2011-03-09
More of a FF question but am hoping to get it resolved here..


My firefox has stopped adding .com to the end of addresses entered I've tried reseting about:config settings (prefix suffix etc) still no joy...

can anyone help?

---

### Post by lithopsian on 2011-03-09
Which version of Firefox do you have right now?

I'm going to guess that your internet keywords function is grabbing the word that you type and sending it to a search engine before it can be fixed up.  Take a look at keyword.enabled and keyword.url.  keyword.enabled will take pretty much anything which doesn't have a dot in it and send it to google (by default).

---

### Post by SlugSlug on 2011-03-09
3.6.15

the search will work for instance if I type

ubuntu forums and hit enter - google brings me here 

if i type ubuntuforums - I get 
**Forbidden**

 You don't have permission to access / on this server.

---

### Post by lithopsian on 2011-03-09
That's why I asked you about the keyword preference.  keyword.enabled means that free text (without a dot, or anything with spaces) will be sent to your configured keyword search engine.  By default this is Google and (I think in 3.6) by default it does a feeling lucky search.  Do when google is confident about matching a single website to your keyword it will send you straight there.  Typing Ubuntu Forums means Google is called to search "ubuntu forums" and Google sends you straight here.

If you type ubuntuforums, all one word, that should also get sent to Google but Google may be sending you somewhere strange.  If that word was treated as a URL and fixed up, you should go to [www.ubuntuforums.com](www.ubuntuforums.com), which is not here.  Where do you actually end up?

---

### Post by SlugSlug on 2011-03-09
i end up at [http://ubuntuforums](http://ubuntuforums)

not . no nothing just forbiden -- same with any site .. natwest / facebook etc etc

about:config keyword.* = set to default

---

### Post by lithopsian on 2011-03-09
That sounds like your DNS, or perhaps a proxy server, is doing funny stuff.  Fixup only happens if a DNS lookup on what you type fails.  If you try to navigate to [http://ubuntuforums](http://ubuntuforums) without any fixup, you should get a server not found error.  Something else is happening if you get a forbidden error.  DNS is presumably succeeding and you are being sent somewhere odd.

What happens if you ping ubuntuforums?

You might have an extension doing weird stuff.  Can you start in safe mode and see if it still does this?

---

### Post by SlugSlug on 2011-03-09
your right with DNS -- ping is adding .co.cc (my domian) to the end of results

i've changed resolv.conf and added nameserver = (router IP ) to /network/interfaces file

still no joy.. ??

---

### Post by SlugSlug on 2011-03-09
you solved it mate, edited out the co.cc in hostname resolve.conf etc rebooted and were cooking again ;)

cheers!!

---

