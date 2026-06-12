---
title: "Script to add brackets around numbers"
date: 2012-01-22
forum: General Help
---

### Post by Kissell on 2012-01-22
I'm stuck writing a BASH script, hoping someone might help out.  I'm reading a file and modifying the file name with my script.  I'm able to do that, but I have one where I only want to change it under a specific condition, and haven't been able to think of a concise solution.

Example File Names:
> 
YourDocument.txt
MyDocs - 11.txt
My Doc 123.html
Vacation Budget - Tokyo.xls


I want to read all those filenames, but I only want to modify "MyDocs - 11.txt".  I want the new filename to be "MyDocs - [11].txt".  It'll add brackets around the number at the end if the number is followed by the space-hyphen-space delimiter.  It won't modify YourDocument.txt because there is no number, and it won't add brackets around 123 because the number wasn't preceded immediately by the " - " delimiter.  

NOTE: The numbers are not always two digit, sometimes they are three, and the delimter occurs in filenames I don't want renamed, such as "Vacation Budget - Tokyo.xls"

TIA

---

### Post by dcstar on 2012-01-23
> **Kissell said:**
> I'm stuck writing a BASH script, hoping someone might help out.  I'm reading a file and modifying the file name with my script.  I'm able to do that, but I have one where I only want to change it under a specific condition, and haven't been able to think of a concise solution.

Example File Names:


I want to read all those filenames, but I only want to modify "MyDocs - 11.txt".  I want the new filename to be "MyDocs - [11].txt".  It'll add brackets around the number at the end if the number is followed by the space-hyphen-space delimiter.  It won't modify YourDocument.txt because there is no number, and it won't add brackets around 123 because the number wasn't preceded immediately by the " - " delimiter.  

NOTE: The numbers are not always two digit, sometimes they are three, and the delimter occurs in filenames I don't want renamed, such as "Vacation Budget - Tokyo.xls"

TIA

```
man sed
```

---

### Post by SuaSwe on 2012-01-23
A start might be something like:

```

suaswe@lxpc~$ cat tmp
YourDocument.txt
MyDocs - 11.txt
MyDocs - 123.txt
My Doc 123.html
Vacation Budget - Tokyo.xls

suaswe@lxpc~$ cat tmp | sed 's_- \([0-9][0-9]*\)_- [\1]_'
YourDocument.txt
MyDocs - [11].txt
MyDocs - [123].txt
My Doc 123.html
Vacation Budget - Tokyo.xls

```

It's very late/early over here and it may need tweaking, but at least it could give you some idea. :D

---

### Post by Kissell on 2012-01-23
> **SuaSwe said:**
> 
It's very late/early over here and it may need tweaking, but at least it could give you some idea. :D

It worked perfectly so far on all my test data without any tweaking.  I use plain old sed a lot for substitutions, but don't script enough to know right away what regexp would work for something like this.  Thanks you very much.

PS: I love that it works, but I'm completely baffled by it.  I can get a general sense of testing for the correct string with numbers in it, but really unclear how it's adding the brackets.

---

### Post by SuaSwe on 2012-01-23
Yay, so glad it worked! :D

Just to explain for anyone who isn't aware, it's the magic of the \(xxx\) character sequence that makes this possible - this sequence grabs the string or regexp between the \( and \) and makes a "segment" out of it that will then be called "\1" (then \2, \3 etc for subsequent segments) in substitution.

A couple of examples: 

```

suaswe@lxpc~$ echo "[COLOR="Blue"]123[/COLOR] [COLOR="Red"]abc[/COLOR]" | sed 's_\([COLOR="Blue"][0-9][0-9]*[/COLOR]\) \([COLOR="Red"][a-z][a-z]*[/COLOR]\)_[COLOR="Blue"]\1[/COLOR] [COLOR="Red"]\2[/COLOR]_'
[COLOR="Blue"]123[/COLOR] [COLOR="Red"]abc[/COLOR]

suaswe@lxpc~$ echo "[COLOR="Blue"]123[/COLOR] [COLOR="Red"]abc[/COLOR]" | sed 's_\([COLOR="Blue"][0-9][0-9]*[/COLOR]\) \([COLOR="Red"][a-z][a-z]*[/COLOR]\)_[COLOR="Red"]\2[/COLOR] [COLOR="Blue"]\1[/COLOR]_'
[COLOR="Red"]abc[/COLOR] [COLOR="Blue"]123[/COLOR]

suaswe@lxpc~$ echo "[COLOR="Blue"]I[/COLOR] [COLOR="Red"]swap[/COLOR] [COLOR="SeaGreen"]words[/COLOR]" | sed 's_\([COLOR="Blue"]I[/COLOR]\) \([COLOR="Red"]swap[/COLOR]\) \([COLOR="SeaGreen"]words[/COLOR]\)_,[COLOR="Red"]\2[/COLOR], .[COLOR="SeaGreen"]\3[/COLOR]. :[COLOR="Blue"]\1[/COLOR]:_'
,[COLOR="Red"]swap[/COLOR], .[COLOR="SeaGreen"]words[/COLOR]. :[COLOR="Blue"]I[/COLOR]:

```

So as long as you can express a string/regexp in such a way that sed knows what you're talking about, you can change its position relative to other strings, enclose it with brackets and insert characters around it at will. Ah, the magic of sed!

---

### Post by Kissell on 2012-01-23
That actually makes sense, and I think I'll be able to use that trick many times in the future.

Why are there underscores in these sed statements?  Is that something that has to go along with these regexps?  I normally only use sed for substitutions like > sed 's/ABC/123/g' and it never has underscores in it when I use it.

---

### Post by SuaSwe on 2012-01-24
The "/"'s (in your case) or "_"'s (in mine) are just delimiters, separating each section of the command from the next - I use underscore because I think it reads clearer than forwardslash, especially when the substitute strings contain backslashes! 

Most characters can be used as delimiters, so long as they don't appear in the string/regexp you're substituting with/for.

So, all of these will return exactly the same result:

```

suaswe@lxpc~$ echo "sub-this" | sed 's_sub-this_for-this_'
suaswe@lxpc~$ echo "sub-this" | sed 's/sub-this/for-this/'
suaswe@lxpc~$ echo "sub-this" | sed 's:sub-this:for-this:'

# all of the above will output "for-this"

```

This one, however, will not work, because the delimiter (a hyphen) is contained within the string:

```

suaswe@lxpc~$ echo "sub-this" | sed 's-sub-this-for-this-'
sed: command garbled: s-sub-this-for-this-

```

This allows you to substitute strings that contain various different characters; so for example if your substitution string contains a forwardslash, you can use underscore or @ or + or something else as a delimiter instead. :) Sed really is quite a nice tool - [[color=blue]this tutorial[/color]]("http://www.grymoire.com/Unix/Sed.html") has some handy tips if you do a lot of file manipulation!

---

### Post by Kissell on 2012-01-24
very cool.  I've always been used to more rigid rules in programming, so I've always been using forward slashes with sed believing it necessary for proper syntax.  thanks so much.  this should make a lot of scripts much clearer to me.

---

### Post by SuaSwe on 2012-01-24
Great stuff! :D

---

### Post by Vaphell on 2012-01-24
when i use more complicated regexes with sed i like to add -r switch for readability. It makes all the regex-related characters not require escaping (or should i say treating them as ordinary characters requires escaping or enumeration in [])
eg
```
$ echo abc123def456 | sed **-r** 's/([0-9]+)/[\1]/'
abc[123]def456
$ echo '---(abc)---' | sed -r 's/([COLOR="Blue"][(][/COLOR]abc[COLOR="Blue"][)][/COLOR])/:\1:/'
---:[COLOR="Blue"]([/COLOR]abc[COLOR="Blue"])[/COLOR]:---
$ echo '---(abc)---' | sed -r 's/([COLOR="Blue"]\([/COLOR]abc[COLOR="Blue"]\)[/COLOR])/:\1:/'
---:[COLOR="Blue"]([/COLOR]abc[COLOR="Blue"])[/COLOR]:---


```
also it's worth mentioning that the part of expression after the last delimiter can be used to define which occurence is to be replaced, eg.
```
$ echo abc123def456 | sed -r 's/([0-9]+)/[\1]/'
abc**[123]**def456
$ echo abc123def456 | sed -r 's/([0-9]+)/[\1]/**2**'
abc123def**[456]**
$ echo abc123def456 | sed -r 's/([0-9]+)/[\1]/**g**'
abc**[123]**def**[456]**
```
none specified is the same as 1, g = all

---

### Post by Kissell on 2012-02-08
Why can I only get regexps to work when I'm using sed?

Like this doesn't print anything, and I think it should:
> 
        if [[ "Hello X00Z99 World" =~ \(X[0-9]Z[0-9]*\) ]] ; then
          echo "Hello World"
        fi


---

### Post by uRock on 2012-02-09
This thread was marked solved. Please start a new thread for your subject.

Thread Closed

---

