---
title: "I want to copy a certain column of text from long list."
date: 2012-03-05
forum: General Help
---

### Post by Rytron on 2012-03-05
Hi.

I have a long list of thousands like so (this is just a sample):

  5   16 Nothocercus bonapartei               Highland Tinamou
  5   17 Nothocercus julius                   Tawny-breasted Tinamou
  5   18 Nothocercus nigrocapillus            Hooded Tinamou
  5   19 Crypturellus berlepschi              Berlepsch's Tinamou
  5   20 Crypturellus cinereus                Cinereous Tinamou
  5   21 Crypturellus soui                    Little Tinamou
  5   22 Crypturellus ptaritepui              Tepui Tinamou
  5   23 Crypturellus obsoletus               Brown Tinamou
  5   24 Crypturellus cinnamomeus             Thicket Tinamou
  5   25 Crypturellus undulatus               Undulated Tinamou
  5   26 Crypturellus transfasciatus          Pale-browed Tinamou
  5   27 Crypturellus strigulosus             Brazilian Tinamou
  5   28 Crypturellus boucardi                Slaty-breasted Tinamou
  5   29 Crypturellus kerriae                 Choco Tinamou

I want to copy just the part "Highland Tinamou" to "Choco Tinamou" into a text file. I copied it into LibreOffice calc but it puts it all in 1 column (I was hoping it would make 4 separate columns). Can someone help me with this? Thanks in advance.

BTW, the list looked like this [attached image] before I pasted it onto this thread.

---

### Post by matt_symes on 2012-03-05
Hi

If i understand you correctly you can use sed for this

```
sed -n '/**Hooded Tinamou**/,/**Thicket Tinamou**/p' **tt** >> **ttt**
```

From your original list

```
matthew@matthew-Aspire-7540:~$ cat tt
5 16 Nothocercus bonapartei Highland Tinamou
5 17 Nothocercus julius Tawny-breasted Tinamou
5 18 Nothocercus nigrocapillus Hooded Tinamou
5 19 Crypturellus berlepschi Berlepsch's Tinamou
5 20 Crypturellus cinereus Cinereous Tinamou
5 21 Crypturellus soui Little Tinamou
5 22 Crypturellus ptaritepui Tepui Tinamou
5 23 Crypturellus obsoletus Brown Tinamou
5 24 Crypturellus cinnamomeus Thicket Tinamou
5 25 Crypturellus undulatus Undulated Tinamou
5 26 Crypturellus transfasciatus Pale-browed Tinamou
5 27 Crypturellus strigulosus Brazilian Tinamou
5 28 Crypturellus boucardi Slaty-breasted Tinamou
5 29 Crypturellus kerriae Choco Tinamou
matthew@matthew-Aspire-7540:~$ cat tt | wc -l
15
matthew@matthew-Aspire-7540:~$ 

```

the above command produced this...

```
matthew@matthew-Aspire-7540:~$ cat ttt
5 18 Nothocercus nigrocapillus **Hooded Tinamou**
5 19 Crypturellus berlepschi Berlepsch's Tinamou
5 20 Crypturellus cinereus Cinereous Tinamou
5 21 Crypturellus soui Little Tinamou
5 22 Crypturellus ptaritepui Tepui Tinamou
5 23 Crypturellus obsoletus Brown Tinamou
5 24 Crypturellus cinnamomeus **Thicket Tinamou**
matthew@matthew-Aspire-7540:~$ cat ttt | wc -l
7
matthew@matthew-Aspire-7540:~$ 
```

You will need to change the bold items for the search terms you want to use and filenames relevent for your system.

Here is a reference for sed that i use.

[http://www.unixguide.net/unix/sedoneliner.shtml](http://www.unixguide.net/unix/sedoneliner.shtml)

Kind regards

---

### Post by Elfy on 2012-03-05
I made a text file - calc imported it using space as a delimiter and it had the columns you expected.

---

### Post by Rytron on 2012-03-05
> **forestpiskie said:**
> I made a text file - calc imported it using space as a delimiter and it had the columns you expected.

Hi forestpiskie (love that username). How did you import the text?

---

### Post by Elfy on 2012-03-05
right click from thunar - open with libre calc -  then you get the import tool

---

### Post by Rytron on 2012-03-05
> **forestpiskie said:**
> I made a text file - calc imported it using space as a delimiter and it had the columns you expected.

How would you get "Highland Tinamou" etc. on the same column?

---

### Post by Elfy on 2012-03-05
Cut or copy the last 2 columns to a new sheet - save as blah - reopen - get the import tool - then remove the space as the delimiter.

Probably an easier bash way to do it - but voodoo expert I am not :)

---

### Post by Rytron on 2012-03-05
> **forestpiskie said:**
> Cut or copy the last 2 columns to a new sheet - save as blah - reopen - get the import tool - then remove the space as the delimiter.

Probably an easier bash way to do it - but voodoo expert I am not :)

Cheers forestpiskie. That did the job. And thank you matt_symes for helping me out.

---

### Post by Elfy on 2012-03-05
> **Rytron said:**
> Cheers forestpiskie. That did the job. And thank you matt_symes for helping me out.

Long winded way I suspect :)

---

### Post by Rytron on 2012-03-05
> **forestpiskie said:**
> Long winded way I suspect :)

Yep. :)

---

### Post by matt_symes on 2012-03-05
Hi

I think i might have misunderstood what you were trying to do when i posted that sed command :( Otherwise i would have posted an awk command.

forestpiskie was right on the ball though ! Thank goodness someone is :)

Kind regards

---

### Post by Rytron on 2012-03-05
> **matt_symes said:**
> Hi

I think i might have misunderstood what you were trying to do when i posted that sed command :( Otherwise i would have posted an awk command.

forestpiskie was right on the ball though ! Thank goodness someone is :)

Kind regards

Feel free to post a code line method if you can.

---

### Post by Elfy on 2012-03-05
> **Rytron said:**
> Feel free to post a code line method if you can.

Absolutely :)

---

### Post by matt_symes on 2012-03-05
Hi

> **Rytron said:**
> Feel free to post a code line method if you can.

You can do something along the lines of

```
matthew@matthew-Aspire-7540:~$ awk '{print $5,$6;}' tt >> tttt
matthew@matthew-Aspire-7540:~$ cat tttt 
Highland Tinamou
Tawny-breasted Tinamou
Hooded Tinamou
Berlepsch's Tinamou
Cinereous Tinamou
Little Tinamou
Tepui Tinamou
Brown Tinamou
Thicket Tinamou
Undulated Tinamou
Pale-browed Tinamou
Brazilian Tinamou
Slaty-breasted Tinamou
Choco Tinamou
 
matthew@matthew-Aspire-7540:~$
```

It assumes there is always 6 columns and those columns are the ones you want.

You're a bird watcher ?

Kind regards

---

### Post by Rytron on 2012-03-05
> **matt_symes said:**
> Hi

You can do something along the lines of

It assumes there is always 6 columns and those columns are the ones you want.

You're a bird watcher ?

Kind regards

Now that is pure genius. Take a bow! ^_-

---

### Post by Elfy on 2012-03-05
> **matt_symes said:**
> Hi



You can do something along the lines of

```
matthew@matthew-Aspire-7540:~$ awk '{print $5,$6;}' tt >> tttt
matthew@matthew-Aspire-7540:~$ cat tttt 
Highland Tinamou
Tawny-breasted Tinamou
Hooded Tinamou
Berlepsch's Tinamou
Cinereous Tinamou
Little Tinamou
Tepui Tinamou
Brown Tinamou
Thicket Tinamou
Undulated Tinamou
Pale-browed Tinamou
Brazilian Tinamou
Slaty-breasted Tinamou
Choco Tinamou
 
matthew@matthew-Aspire-7540:~$
```

It assumes there is always 6 columns and those columns are the ones you want.

You're a bird watcher ?

Kind regards

Oh no - I managed to get some voodoo to work :( 

Thanks from me matt_symes :)

---

### Post by Rytron on 2012-03-05
> **matt_symes said:**
> You're a bird watcher ?Kind regards

No but I love learning about animals and all things from the natural world.

---

