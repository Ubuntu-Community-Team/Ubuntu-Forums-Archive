---
title: "How to for wiki"
date: 2010-09-23
forum: General Help
---

### Post by Silvernail on 2010-09-23
Is there a 'Wiki for Dummies'? Everything I have found so far deals with configuration. I want to know how do I:

1. format a page
2. what to do with .css pages
3. how do I get images to display

This will get me started on finding out what I don't know.

Many thanks for what ever direction you can point me.
Dave

---

### Post by luigi_mb on 2010-09-23
I use WOAS from

[http://stickwiki.sourceforge.net/](http://stickwiki.sourceforge.net/)

Very good, easy to install (just unzip in your home folder), well documented.


/luigi

---

### Post by Silvernail on 2010-09-24
Thanks for the suggestion. Stickwiki is a client side application and will not work on a remote server.

I have mediawiki installed on my computer to test it.

This HTML code snippet
```
<hr/>
<h2>Portuguese Man O'War</h2>
<img src="Sailing MOW.JPG" align="left" alt="Man O'War at sail" /><img src="Underside MOW.JPG" align="right" alt="Underside MOW" />

<p>The Portuguese Man O'War is not a jelly fish, although it is commonly called that <a href="http://en.wikipedia.org/wiki/Portuguese_Man_o%27_War">Wiki</a>, but it can hurt you. If you go to the beach and see this creature in the water, turn around and go someplace else.</p>

<p>This creature is pushed through the water by the wind on it's air bladder or carried along by the tidal movement. Notice the tentacles on the under side of the PMOW, these can extend out to 40 feet on a large one. The PMOW captures it prey by stinging it. For a human this can be a very excruciating painful experience. On a small child or adult with heart problems, it may be fatal. For a medium sized child, they are going to be in a state of panic and severe pain. I have seen adults with tears in their eyes from just one tentacle clinging to their arm</p>
<img src="Dead MOW.jpg" align="left" alt="Dead Man O'War" /> <p>Even when dead or dieing, they are still dangerous. Avoid any stranded on the beach.</p>
<p>There are a couple of things you can do to alleviate the burning sensation of the sting. One is apply a mixture of baking soda and amonia. Thats hard to carry on a trip to the beach. Better is to cover well with 'Adolphs Meat Tenderizer".</p>
<p>Keep a BOTTLE in your first kit - YOU DO HAVE ONE, DON'T YOU?</p>
</td>
</tr>

```

After being run through 'html2wiki.sh' it this snippet.
```

=Portuguese Man O'War==

[[Image:Sailing%20MOW.JPG|Man O'War at sail]][[Image:Underside%20MOW.JPG|Underside MOW]]

The Portuguese Man O'War is not a jelly fish, although it is commonly called that [[Portuguese Man o' War|Wiki]], but it can hurt you. If you go to the beach and see this creature in the water, turn around and go someplace else.

This creature is pushed through the water by the wind on it's air bladder or carried along by the tidal movement. Notice the tentacles on the under side of the PMOW, these can extend out to 40 feet on a large one. The PMOW captures it prey by stinging it. For a human this can be a very excruciating painful experience. On a small child or adult with heart problems, it may be fatal. For a medium sized child, they are going to be in a state of panic and severe pain. I have seen adults with tears in their eyes from just one tentacle clinging to their arm

[[Image:Dead%20MOW.jpg|Dead Man O'War]]

Even when dead or dieing, they are still dangerous. Avoid any stranded on the beach.

There are a couple of things you can do to alleviate the burning sensation of the sting. One is apply a mixture of baking soda and amonia. Thats hard to carry on a trip to the beach. Better is to cover well with 'Adolphs Meat Tenderizer".

Keep a BOTTLE in your first kit - YOU DO HAVE ONE, DON'T YOU?
|-
|

|-
|
----

```

1. How do I align the images left or write?
2. Css was told to make certain size (H1) fonts a certain color. That did not happen.
3. I don't want a table of contents at all. How to eliminate?

These are the type of things I need to know where to find out how to do?
Again, thanks for trying  to help.
Dave

---

