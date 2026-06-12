---
title: "Add Parenthesis Around Word in Script"
date: 2011-08-19
forum: General Help
---

### Post by Kissell on 2011-08-19
I have a bunch of strings with a four digit year in them, and I want to add parenthesis around the year, so "This is my life 2009.txt" would become "This is my life (2009).txt"

I wrote the following solution...  It works, however, it is not very elegant.  It takes up lots of lines of code, and only works between the years 2010 and 2018.   

Occasionally there might be more than one year in the string, in that case, I want to act upon the right-most year only (my solution currently doesn't address that issue).  

Sometimes there is no year at all in the string...  in that case the program needs to continue with the string unmodified.

Can someone help me finish this up?  Here's my solution, it works for the most part...  just wondering how others would have solved the problem so that I can learn.

> 
STRINGY_STR="This is my life 2009.txt"
INPUT_PAREN=$(echo $STRINGY_STR|sed -e 's/2018/(2018)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2017/(2017)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2016/(2016)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2015/(2015)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2014/(2014)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2013/(2013)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2012/(2012)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2011/(2011)/g')
INPUT_PAREN=$(echo $INPUT_PAREN|sed -e 's/2010/(2010)/g')


---

