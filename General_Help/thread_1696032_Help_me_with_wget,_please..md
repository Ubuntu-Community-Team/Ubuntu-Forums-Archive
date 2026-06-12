---
title: "Help me with wget, please."
date: 2011-02-26
forum: General Help
---

### Post by yangjiangnan on 2011-02-26
I want to download the contents (gene sequences) of NCBI websites. e.g.:
http://www.ncbi.nlm.nih.gov/nuccore/NC_015089.1?report=fasta&log$=seqview&format=text
or 
[http://www.ncbi.nlm.nih.gov/nuccore/NC_015089](http://www.ncbi.nlm.nih.gov/nuccore/NC_015089)

I can see the contents of these websites when I use Firefox. But when I use 
wget the.above.url
I can only get an empty file or a file of general introduction to NCBI. How can I use wget the get the sequences I want? I have hundreds of sequences to download, so I want to use command line to do it automatically. If wget does not work for me, is there any other suggestions?
Thanks!

---

### Post by down_to_earth_sort_of_guy on 2011-02-26
This happens because there is a bit of javascript which runs and dynamically fetches the _actual_ content and inserts this into the webpage at runtime.

This is a simplistic method to prevent someone from downloading the content.

It is still possible to get the actual content, just needs a little bit of imagination and a simple script ;-)

btw ... there must be a legal way to do this as it looks like they don't want anyone ripping this content!

---

### Post by yangjiangnan on 2011-02-27
> **down_to_earth_sort_of_guy said:**
> This happens because there is a bit of javascript which runs and dynamically fetches the _actual_ content and inserts this into the webpage at runtime.

This is a simplistic method to prevent someone from downloading the content.

It is still possible to get the actual content, just needs a little bit of imagination and a simple script ;-)

btw ... there must be a legal way to do this as it looks like they don't want anyone ripping this content!

Thanks!
I managed to do it. I think NCBI resources are free, they have no reasons to prevent scientists to do research conveniently. There is a link they provided to generate a file to download manually. But when I copied that link and passed it to wget, it worked!

---

