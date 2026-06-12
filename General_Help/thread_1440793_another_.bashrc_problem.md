---
title: "another .bashrc problem"
date: 2010-03-27
forum: General Help
---

### Post by megamark on 2010-03-27
okay, im just starting to do functions in my .bashrc file. i added the code [FONT=Verdana]
[/FONT]function today {
> echo "Today's date is:"
> date +"%A, %B %-d, %Y"
> }

into my .bashrc file and logged back in to see if it ran. it didnt. 
i have legit .profile i checked that. help please...

---

### Post by superyounan1 on 2010-03-27
it isn't enough to define a function, you have to call it also.

---

### Post by kaibob on 2010-03-27
I agree with superyounan1 that you have to call the function. For example, I put the following in my ~/.bashrc file:

```
function today {
echo "Today's date is:"
date +"%A, %B %-d, %Y"
}
```

I then opened a terminal window and entered today:

> $ today
Today's date is:
Saturday, March 27, 2010

---

### Post by megamark on 2010-03-28
ooooh. i was under the impression that it started automatically when i logged in. i can call it successfully. thanks guys.

---

