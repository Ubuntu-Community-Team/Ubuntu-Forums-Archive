---
title: "some advanced text processing/html"
date: 2011-07-29
forum: General Help
---

### Post by vangop on 2011-07-29
Hi guys,
I have a bunch of htmls that have a part I want to remove.
This part is a div with nested divs, so I can't use a regex with sed, (like s/<div id="toc".*</div>//g) since the closing /div will match the ending of the 1st sibling.
(or if this requires some deeper knowledge of sed I obviously lack it).

I know the xpath expression of the part I want to remove.
There's an xpath tool, but it only prints the xpath, not removes it. Also the html is not strict xhtml, so xpath would fail anyway.
Can you plz suggest something?

---

### Post by galvatron408 on 2011-07-29
can you post an example of what it really looks like and a sample of how you want it to look like?

---

### Post by bodhi.zazen on 2011-07-29
You could probably do it with awk (see gsub) or perl, but you need to know the substitution you need to make.

---

### Post by vangop on 2011-07-30
Yes, this is the site I want to process.
[http://developer.android.com/guide/index.html](http://developer.android.com/guide/index.html)
I want to delete the left navbar, div id="side-nav". this div has nested divs..
I could use perl/awk if I knew them )
The only solution I found now is to find the line the div starts, find the ending line and delete the lines between with sed -e X,Yd
this works only because those numbers are the same in all htmls, wonder if there's a better solution.

---

### Post by galvatron408 on 2011-07-30
well, I still don't know what you want to do but this perl script will print everything that begins with anything+<div id=

----------------------------
cat sample.pl 
open (FILE, "index.html");
@test=<FILE>;
close FILE;

foreach (@test){
print "$_\n" if $_ =~m/^.*\<div id=/ig;
}
-----------------------------


This is what happens when I run it through that link you provided...
curl [http://developer.android.com/guide/index.html](http://developer.android.com/guide/index.html) | perl sample.pl
  <div id="header">

      <div id="headerLeft">

      <div id="headerRight">

          <div id="headerLinks">

  <div id="search" >

      <div id="searchForm">

                  <div id="search_filtered_div" class="no-display">

      <div id="devdoc-nav">

<div id="jd-header" class="guide-header">

  <div id="jd-content">

<div id="footer">

  <div id="copyright">

  <div id="build_info">

  <div id="footerlinks">


See? now you can say.... omit "<div id" or do whatever you wish to do. Not what you were looking for? post a Before and After and I'll see what I can do.

---

### Post by galvatron408 on 2011-07-30
oooh, the forum chopped all leading spaces on the <div... hehe

---

### Post by bodhi.zazen on 2011-07-30
Same thing with awk

```
awk '/div id/ {print $0}' index.html
  <div id="header">
      <div id="headerLeft">
      <div id="headerRight">
          <div id="headerLinks">
  <div id="search">
      <div id="searchForm">
                  <div id="search_filtered_div" class="no-display">
      <div id="devdoc-nav">
<div id="jd-header" class="guide-header">
  <div id="jd-content">
<div id="footer">
  <div id="copyright">
  <div id="build_info">
  <div id="footerlinks">
```

but that did not show your side-nav

so, using grep I found it ...

```
awk '/div class.*side/ {print $0}' index.html
    <div class="g-unit g-first" id="side-nav">
```

But again, we sort of need to know the substitution ...

looking at your file, I assume you want to delete the entire side bar ?
```
sed -e "/<div class=\"g-unit g-first\" id=\"side-nav\">/,/<\!-- end side-nav -->/c `echo deleted`" index.html > index2.html
```

try index2.html , if it works, run this


```
sed -e "/<div class=\"g-unit g-first\" id=\"side-nav\">/,/<\!-- end side-nav -->/d" index.html > index3.html
```

index3.html should be close to what I think you want, if no let us know.

---

### Post by vangop on 2011-07-30
Hi guys,
thanks for your suggestions!
Yes, like I said I wanted to remove the whole left navbar, which is the div with id side-nav. So that one-line sed is what works for me perfectly. 
Since I'm doing a lot of html processing/cleaning to make books for ereader from sites, was wondering about a way to do things in general.

Even though it worked in this case because there was a comment 
<\!-- end side-nav -->
it wouldn't AFAIK in general case when I need to delete a particular div with all subelements, since it seems not possible to make a regexp to match it fully. (consider the same example, without that end side-nav)
Ideally is to be able to manipulate html with xpath-like style (delete based on xpath). Do you think it is possible with sed/awk/perl without writing large scripts or is there any more suitable tool?
Thanks!

---

### Post by bodhi.zazen on 2011-07-30
At the end of the day, you have to have something unique to match on. 

This is on reason why you use things such as comments and id=

I do not know any tool that is going to to do this for you based on xpath, but I did find this discussion via a google search :

[http://stackoverflow.com/questions/6837892/remove-pbr-p-with-domxpath-or-regex](http://stackoverflow.com/questions/6837892/remove-pbr-p-with-domxpath-or-regex)

---

