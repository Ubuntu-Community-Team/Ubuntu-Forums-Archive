---
title: "Bash  Scripting and the Web"
date: 2012-02-26
forum: General Help
---

### Post by LinuXofArabiA on 2012-02-26
Hello Veterans and Gurus,

I have been learning bash for the past couple of weeks, and need help with an idea that I had. I basically want to write a script to download the first ten pages of a Google search for a keyword of my choice. 
The idea basically is to have a program that does a very primitive form of web crawling for me. This way, I could download the content of the web, and do my data mining for it later. 

This is the idea in very general headlines. It is still not quite crystal clear in my own head to be able to present it as a detailed question, but in essence, as a start I want to be at least be able to do what I mentioned above.

Any idea how bash scripting could help with that? Is there any reading material that would educate me on scripting commands specifically for interfacing with the web and its content? Is bash script the way to go in the first place?

I realize these are broad questions, so feel free to respond with broad answers. I would be happy to go in any direction this thread heads. 

Also feel free to throw in any terminal commands that you think might be relevant or helpful. My list of terminal commands has no limit.

---

### Post by Lars Noodén on 2012-02-26
You could read up on [wget](http://manpages.ubuntu.com/manpages/oneiric/en/man1/wget.1.html), but it is more likely that you'll need to parse the HTML to get at the link for the next page.  To do that you'll need an actual XHTML parser like perl's [HTML:: Parser](http://search.cpan.org/dist/HTML-Parser/) or HTML::LinkExtor

---

### Post by LinuXofArabiA on 2012-02-26
wget is actually a great place to start! I started reading up on it and it is definitely going to be useful. Thanks. 

I hope more people chime in with their expertise.

---

### Post by greenpeace on 2012-02-26
Hi, 

I would actually be tempted to do this in the scripting language Python[1], rather than Bash.  

I find that Python is easy to understand, maintain, and has some really useful libraries, including:

[LIST]
[*]urllib2[2] for opening connections and downloading webpages
[*]BeautifulSoup[3] for HTML parsing
[/LIST]

In addition there are excellent tutorials for getting you started.

good luck!


[1] [http://www.python.org/doc/](http://www.python.org/doc/)
[2] [http://docs.python.org/library/urllib2.html](http://docs.python.org/library/urllib2.html)
[3] [http://www.crummy.com/software/BeautifulSoup/bs4/doc/](http://www.crummy.com/software/BeautifulSoup/bs4/doc/)

---

### Post by Khayyam on 2012-02-26
LinuXofArabiA ...

I'm not sure google provides scrapable URL's (except perhaps adds and internal google services). See for yourself:

[url_scrape.py]("http://madphilosopher.ca/doc/url_scrape_py.txt")

```
#!/usr/bin/env python

'''Returns a list of URLs that are found in standard input.

These URLs must be between quotes ("" or '') and must start with http://

Modified from Python Recipe 30270 by Yuriy Tkachenko:
http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/302700

'''

__RCS__ = '$Id: url_scrape.py,v 1.4 2005/06/19 18:18:34 darren Exp darren $'
__version__ = '$Revision: 1.4 $'
__initialdate__ = 'June 2005'

__author__ = 'Darren Paul Griffith, http://www.madphilosopher.ca/'

import re
import sys


if __name__ == '__main__':

    # Pattern for fully-qualified URLs:
    url_pattern = re.compile('''["']http://[^+]*?['"]''')

    # build list of all URLs found in standard input
    s = sys.stdin.read()
    all = url_pattern.findall(s)

    # output all the URLs
    for i in all:
        print i.strip('"').strip("'")
```Wrap it together with bash/wget (wgeturl.sh) ...

```
!/bin/bash

if [[ -z ${@} ]]; then
    echo "No search string provided!"
    echo "Usage: $(basename ${0}) <search string>"
    exit
fi

wget -U mozilla -q -O - 'http://www.google.com/search?q='"${@}" | url_scrape.py >> urls.txt
```

The run 'wgeturl.sh <search string>'
 
I may be wrong but I think they obfusticate URL's in order to "[not be evil]("http://en.wikipedia.org/wiki/Don%27t_be_evil")".

best ... khay

---

### Post by Lars Noodén on 2012-02-27
Google's search API might or might not useful here too:

[https://code.google.com/apis/customsearch/](https://code.google.com/apis/customsearch/)

---

