---
title: "Making fortune files - why is this screwing up and how do i fix?"
date: 2010-04-07
forum: General Help
---

### Post by tehschulman on 2010-04-07
right now I'm editing a collection of text files for use with fortune to display quotes from some tv shows i like. with building fortunes, once you generate the plaintext file full of the fortune quotes you need to generate a .dat file to go with it that stores the randomizing information for that particular set.

i try to run the following however, and for all the dozens of quotes in my text file the .dat file only contains 1 string:

```
strfile homemovies homemovies.dat
```

all the quotes are separated by '%' like they should be, there is a % at the end closing out the last quote, it's saved as a plaintext file, but strfile isn't recognizing the data properly.

i did edit this file using windows notepad, but have resaved it with gedit as a plaintext file and still no go. wtf is going on?

---

### Post by darolu on 2010-04-07
Try with:
```
strfile -iors homemovies homemovies.dat
```

---

### Post by tehschulman on 2010-04-07
Nope, still getting the same output (though -r would be useful in this case). Output is:

```

dmschulman@knox:~$ strfile -ior homemovies homemovies.dat"homemovies.dat" created
There was 1 string
Longest string: 36613 bytes
Shortest string: 36613 bytes

```

---

### Post by tehschulman on 2010-04-07
Hmm seemed to fix it. Something to do with character encoding. Pasted it in to google docs and copied to the text file and that did the trick.

---

