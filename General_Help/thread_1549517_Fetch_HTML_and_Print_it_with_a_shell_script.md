---
title: "Fetch HTML and Print it with a shell script"
date: 2010-08-09
forum: General Help
---

### Post by kongcsr on 2010-08-09
here is the scenario:
i want to use a shell script (run by a daily cronjob) to have a morning newspaper waiting in my printer tray by 7AM.

Details:
So far, I have got a cron manager installed on my computer to run a command on specified times. 
what i want to do is create a shell script that downloads an HTML file every morning and prints it out through my HP printer.
the HTML file can reside on an outside server, or even locally. i plan  to use an HTML file consisting of included RSS feeds like Wired and  Newser, and other details such as the weather forecast and the date.

if this can be done through the cron manager, that is great, but i can't  find the command for cron to print an html page to save my life, and  since it is easier to get cron to execute a single command, the logical  plan is to use something like './HTMLnews.sh' where the batch file  contains instructions to call up server.com/htmlNews.html and then print  out the page after it loads.

seems really simple..but we'll see.

---

### Post by Dustin2128 on 2010-08-09
alright, first you'll need
```
wget http://newspaperurl.url
```that obviously downloads the site. As for how to time it I'm not entirely sure, probably something like ```
if ($hour = x) then wget... && print
```as for printing, check out this [thread.]("http://ubuntuforums.org/showthread.php?t=550483")

I'm interested in what other people will post to this thread, subscribed.

---

### Post by earthpigg on 2010-08-09
well, downloading the entire website may be a bit much.

maybe combine the -r flag for recursive with the --level flag for depth.

wget -r --level=2 [http://whatever.com](http://whatever.com)

would download the main page, and anything linked to on that page. i think.

---

### Post by kongcsr on 2010-08-10
ok,so now that we know we can use wget to fetch the html file, (its only one file to be printing a one page newpaper)

what is the command to send that to the printer?

im thinking the pipe - | symbol will come into play to output the html into a print job somehow in the dev folder.

im totally guessing at this point though.

---

### Post by kongcsr on 2010-08-10
i just checked out that thread that you posted, and i just installed LPR

now that we know the command and programs to use to get it printing, lets take a look at what kind of code we are going to use and if it will work or not.

#!/bin/bash
sudo wget [http://server.com/page.html](http://server.com/page.html)

(insert code here to define where the html page gets saved on the local hard drive)

lpr /path/to/page.html

#end

ok OR would it be better for me to just...

sudo wget [http://server.com/page.html](http://server.com/page.html) | lpr

the last post on the thread about lpr, some guy said that you could pipe the output of a command into lpr and i think that if you can wget something, then maybe you can pipe the output through lpr.

my only issue and stipulation is that it come out as HTML output, and not plaintext html code, which would be a little bit like reading the matrix on my way to work to get some simple news. lol.

---

### Post by kongcsr on 2010-08-10
im starting to think that it is going to print out plain text html as i have just tested it and then run sudo ./page.html and it just gave me a bunch of plaintext, aalthough when i ran 'firefox ./page.html it came out in firefox as a normal web page would.

how would i then get the firefox output to go to the lpr program?

---

### Post by kongcsr on 2010-08-11
anybody?

---

