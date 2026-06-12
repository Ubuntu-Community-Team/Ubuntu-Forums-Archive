---
title: "Trying to write a script to grab info off website"
date: 2009-07-20
forum: General Help
---

### Post by yaazz on 2009-07-20
Hi there, I am trying to write a command line script to scrape specific lines of text off of a website, and then write them to a file. 

To explain better, look at this website [http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a]("http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a")  

I want to have a line in a file say something like 
Piedmont Bidet, Deck Mount;Bidets;BT500AR;Contemporary;Vitreous china bidet complete with mounting bolt caps.;

I have permission to do this, and was told to do it by hand, but that sounds terrible.... 

So what I have done is downloaded the page for offline viewing with wget (although I just need the source file firefox displays, is it possible to get this without downloading everything?)

then using sed, I parse through the info on the site, grabbing what I need. 
Now, my sed script might look a little bit specific but the site is the same on every single page, so it seems to work on a number of different products on the site.  ignore the cat line as that is just printing out the downloaded webpage.

cat Default.aspx\?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21\&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a.html | sed 's/<span class="BreadCrumbHeader">You Are Here: <\/span><span class="BreadCrumbLink"><a href=.http:\/\/www.totousa.com\/.*goto.>\([a-zA-Z]*\)<\/a><\/span>'/\1/

the line I am trying to print off is somewhere around line 329 in the source code of the site.   
What I am trying to do in the line above, is just extract the word "bidets" from the line. so I am using reg epressions to "remember" this line, then replace the whole line with "bidets". the part of the script where I do this is \([a-zA-Z]*\)   then when replacing with \1 it should print off that character string. Unfortunately when I do this my script is literally printing off "1"! why is it doing this?


if you could help this would be great! if not thanks for taking the time to read my post

---

### Post by MikeSD on 2009-07-20
I think it would be much easier to write it in PHP than in shell script.
I do lots of stuff in PHP, on Ubuntu I have installed XAMPP for development - it will give you PHP, MySQL, Apache easily so you could develop anything like that.

---

### Post by Niksko on 2009-07-20
My suggestion would be to use an app called curl. This will grab the html code of the page. You could then pipe that to grep and sed and filter out the bits that you're interested in.

I'm no expert at using grep or sed, so someone else would have to help out with that, but the syntax to get that page would be:
```
curl -s --connect-timeout 30 "http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a" 
```

Curl can be found in the repos

-Nik

---

### Post by yaazz on 2009-07-20
I am pretty familiar with LAMP, and have a bunch of PHP experience, but I have no idea how you would go about doing this with PHP. would you be able to start me off in the right direction?

---

### Post by p0cky84 on 2009-07-20
This can easily done in python,  just take a look at the [string module]("http://docs.python.org/library/string.html") and the[ urllib module]("http://docs.python.org/library/urllib.html").
Combine those two and you'll have yourself a script in 1 hour.

From string use the find() function, and from urllib you'll need the urlopen() function.
And please don't tell me that you can't do it and buhu cause you really wanted someone else to do it for you, this is a really good way to learn how to work individually, and don't have to rely on other people.
Soon you'll be able to write lotsa scripts and programs for yourself.

Good luck.

EDIT: 
@MikeSD, PHP? Thats the dumbest crap I've ever heard.
 
@yaazz: **Do not** listen to this man.

---

### Post by benj1 on 2009-07-20
what about

```
wget 'http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a' --output-document=- | grep -n  bidet > bidet.txt
```

will just give you lines and line numbers with 'bidet' in it, may need some work to get rid of tags in you need ( check man page for 'tr')


@niksko
why curl? isn't that basically the same as wget which is installed by default?

---

### Post by yaazz on 2009-07-20
that would work in this specific case, but there is no guarantee it says "bidets". thats why it is [a-zA-Z]*

---

### Post by wojox on 2009-07-20
Use php. Read the file into a string with file_get_contents.
Then extract between to delimiters.

---

### Post by Celauran on 2009-07-20
> **p0cky84 said:**
> This can easily done in python,  just take a look at the [string module]("http://docs.python.org/library/string.html") and the[ urllib module]("http://docs.python.org/library/urllib.html").
Combine those two and you'll have yourself a script in 1 hour.

+1

You'll probably want to include re as well to help with the parsing.

---

### Post by yaazz on 2009-07-20
I am currently reading python tutorials. I think i have avoided learning this language long enough, it seems very useful. 

PHP way seems like it would work, but I am just going to use this opportunity to learn python. 

One thing I can't seem to figure out, is how to get the output of the website as a variable, and not print it to a file?

---

### Post by sisco311 on 2009-07-20
i would use w3m+awk. something like:
```
w3m "http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a" | awk '$1=="You" && $2=="Are" && $3=="Here:" || $1=="Category"{getline;print}'

```

---

### Post by Celauran on 2009-07-20
> **yaazz said:**
> 
One thing I can't seem to figure out, is how to get the output of the website as a variable, and not print it to a file?

```
variable_name = urllib2.urlopen(url_goes_here).read()
```

---

### Post by yaazz on 2009-07-20
wow w3m is amazing, definitley what I am going to use thanks!

---

### Post by yaazz on 2009-07-20
> **sisco311 said:**
> i would use w3m+awk. something like:
```
w3m "http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=43c7d00c-76b4-4bc9-9347-ba67e7378e21&SearchId=563a7491-9c24-4c35-80df-0cba40d3ac9a" | awk '$1=="You" && $2=="Are" && $3=="Here:" || $1=="Category"{getline;print}'

```


only thing is I am not very familliar with AWK, could you explain your command really quickly?

awk '$1=="You" && $2=="Are" && $3=="Here:" || $1=="Category"{getline;print}'

---

### Post by prem1er on 2009-07-20
Check out this resources if you are planning on working with shell scripts. It will be very useful to you I think.

[http://docstore.mik.ua/orelly/unix2.1/sedawk/index.htm](http://docstore.mik.ua/orelly/unix2.1/sedawk/index.htm)

---

### Post by yaazz on 2009-07-20
Ive used awk before just not for a few years. 

if I were to guess 
awk '$1=="You" && $2=="Are" && $3=="Here:" || $1=="Category"{getline;print}' 

so it checks for you are here: and prints off that line, then if it encounters category, it gets the next line and prints it?

---

### Post by sisco311 on 2009-07-20
```
awk '[COLOR="Red"]$1" "$2" "$3=="You Are Here:"[/COLOR] [COLOR="Blue"]||[/COLOR] [COLOR="SandyBrown"]$1=="Category"[/COLOR]{[COLOR="Yellow"]getline[/COLOR];[COLOR="Purple"]print[/COLOR]}'
```

[color="Red"]if the line begins with "You Are Here"[/COLOR] [COLOR="Blue"]OR[/COLOR] [COLOR="SandyBrown"]with "Category"[/COLOR], then [COLOR="Purple"]print[/COLOR] [COLOR="Yellow"]the next line[/COLOR]

---

### Post by yaazz on 2009-07-21
another question, I would like to grab the bulleted points, but cant get a pattern that I can match to grab it. there is the little ac character but awk doesn't seem to want to match it

Then I want to grab the small description underneath. Can I still use awk to do this? 

does anyone know how to do this

---

