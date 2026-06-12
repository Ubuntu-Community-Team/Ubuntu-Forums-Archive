---
title: "help with sed"
date: 2010-12-18
forum: General Help
---

### Post by d3zz on 2010-12-18
hello people! 

i'm trying to make a bash script but the sed command is bringing me down.

this is the text i want to edit with sed

```

http://www1308.megaupload.com/files/e1f95eac44f602ffe64d6933f7c54b33/the.daily.show.2010.12.16.hdtv.xvid-fqm.avi" class="down_butt1"onclick="javascript:window.open('http://s.megaclick.com/ad.code?de=5b54d530-84fd7c7b-e46c6697-286ab7c4-abe2-3-a279&tm=1292687827.74164&du=aHR0cDovL3J0cy5wZ21lZGlhc2VydmUuY29tLzRmNjFkZC8%3d%0a','popunder','width=800,height=800,scrollbars=yes,status=no,resizable=yes, toolbar=no'); window.focus();"></a></div>

```how do i get rid of everything but the first link?

i tried:
```
sed 's/"  class="down_butt1"onclick="javascript:window.open('http://s.megaclick.com/ad.code?de=5b54d530-84fd7c7b-e46c6697-286ab7c4-abe2-3-a279&tm=1292687827.74164&du=aHR0cDovL3J0cy5wZ21lZGlhc2VydmUuY29tLzRmNjFkZC8%3d%0a','popunder','width=800,height=800,scrollbars=yes,status=no,resizable=yes,  toolbar=no'); window.focus();"></a></div>//'
```but i only got various errors i fixed just to get another error. i even got to the point where the terminal after typing my command just went:
>
>
>
>
>

what is that and how do edit the text right?

---

### Post by TeoBigusGeekus on 2010-12-18
Save the text to a file called string.
The script I've come up with is this (my preferred method is dummy files):
```
#!/bin/bash
#replace double quotes with newline, thus isolating the address
sed -i 's/"/\n/g' string
#save the line with the www string into a new file called string1
grep www string > string1
```

---

### Post by The Cog on 2010-12-18
If you posted the correct string, then it looks like you want to drop everything after the first double-quote ("). This should do it:
```
sed 's/".*//'
```

---

