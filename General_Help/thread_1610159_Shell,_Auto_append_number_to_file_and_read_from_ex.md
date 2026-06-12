---
title: "Shell, Auto append number to file and read from external file."
date: 2010-10-31
forum: General Help
---

### Post by ironic.demise on 2010-10-31
```
cat ${SOURCE}/{start,universal,index,end}.txt > ${SERVER}/index.html
	cat ${SOURCE}/{start,universal,02042010,end}.txt > ${SERVER}/02042010.html
	cat ${SOURCE}/{start,universal,11042010,end}.txt > ${SERVER}/11042010.html
	cat ${SOURCE}/{start,universal,downloads,end}.txt > ${SERVER}/downloads.html
	cat ${SOURCE}/{start,universal,gallery,end}.txt > ${SERVER}/gallery.html
	cat ${SOURCE}/{start,universal,15042010,end}.txt > ${SERVER}/15042010.html
	cat ${SOURCE}/{start,universal,24042010,end}.txt > ${SERVER}/24042010.html
	cat ${SOURCE}/{start,universal,05052010,end}.txt > ${SERVER}/05052010.html
	cat ${SOURCE}/{start,universal,maplestory_and_ubuntu_lucid,end}.txt > ${SERVER}/maplestory_and_ubuntu_lucid.html
	cat ${SOURCE}/{start,universal,first_tattoo_and_new_baby,end}.txt > ${SERVER}/first_tattoo_and_new_baby.html
	cat ${SOURCE}/{start,universal,getting_fatter,end}.txt > ${SERVER}/getting_fatter.html
	cat ${SOURCE}/{start,universal,moved_home,end}.txt > ${SERVER}/moved_home.html
	cat ${SOURCE}/{start,universal,about_writer,end}.txt > ${SERVER}/about_writer.html
cat ${SOURCE}/{start,universal,second_scan,end}.txt > ${SERVER}/second_scan.html
```

How could I get this shell file to:
a.instead of ask for a filename instead just append it with 1,2,3,4,5 etc. after the last file?
b. put each page into a seperate file i.e
```

sites:
second_scan
aboutwriter
movedhome
```
and read it into the script?

so
```

cat ~/list | cat ${SOURCE}/{start,universal,*,end}.txt > ${SERVER}/*.html
```

That way I can avoid having to remember the last filename and I can add an exit 0 onto the script to utilize proper exiting.

---

### Post by ironic.demise on 2010-11-01
bump

---

### Post by KeyserSoze93 on 2010-11-01
I think I can see what you are trying to do; your trying to concatenate a static beginning and end around a different main content section to construct pages of your website.

But I'm trying to understand what you mean about appending numbers to the previous filename since I can't see an example of that behaviour in your output.

Presumably there's not a straight forward 1, 2, 3 etc. progression of dates - the only numbers I can see - since you don't blog every day.

---

### Post by ironic.demise on 2010-11-01
Well, Rather than me have to name each page, for them to just number themselves.
I.E. My homepage now (index.html) will be called "volunteering", and the page after that will be called "Latest news" and so on and so forth.
Instead of having them named, have them so it goes 1.html, 2.html, 3.html in the order they were created.

That way my homepage, the link to the previous blog entry would be href=12.html, and 12.html would link to 11.html...

Does that make more sense?

---

