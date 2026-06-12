---
title: "Linux software for making printable adds/flyers?"
date: 2011-07-14
forum: General Help
---

### Post by Syndicalist on 2011-07-14
I need to create and print some fliers for an event our organization is putting out. I need my application to do the following.

1. Use an image as background, or the ability to scale an image to an area of the background. 

2. Type in various fonts in large bold text super imposed on the background. I need a lot of control over where its placed as it cant be in paragraph formating. 

3. Insert images of mixed format into squares of a predetermined size, made to fit, cropped instead of stretched.

.....that should do it.


It might be possible with libre office or open office, but I am wondering if there are either some convenient ready made flier templates or else some other lesser known programs that can help make this easy and intuitive.

I didnt see a section for 'applications', so you can move this if it belongs somewhere else.

---

### Post by CatKiller on 2011-07-14
The GIMP can do all of that. There's a bit of a learning curve, but if you've used an image creation program before you should be able to find everything.

---

### Post by foxmulder881 on 2011-07-14
All you need is GIMP. :p

---

### Post by szal on 2011-07-14
You might even be lucky that LibreOffice Writer does all that already. A bit more of a learning curve would be doing it in LaTeX or Scribus.

---

### Post by foxmulder881 on 2011-07-14
Take my advice from someone who works on the imaging industry, avoid Scribus. You'll end up crying back here with problems.

---

### Post by Syndicalist on 2011-07-15
I use gimp for photo editing a lot. Im not surprised that GIMP is able to do all that. Can anyone tell me which options I should be using for each of my 3 steps?

Would I be better off using different apps for different stages? Is gimp really best for the lettering?


Finally, besides finding a template for Libre office, is it possible that there is a smaller and more focused application besides GIMP that is simpler for making fliers and business cards? It seems like a common enough thing to be doing that there would be a few alternatives.


Where would I look for templates for Libre Office for this?

---

### Post by CatKiller on 2011-07-15
> **Syndicalist said:**
> Is gimp really best for the lettering?

Maybe, maybe not. I've tend to find that in the time it would take me to get used to a potentially more efficient tool, I could have already done whatever it was with the tool that I'm already used to.

You could try Inkscape (vector graphics creation). I've not used it much, but ISTR that it was quite configurable for blocks of text, and obviously you can always move things around as much as you want with whatever you use. Fiddle with your text and export it as a raster image to use as a layer in The GIMP. For that matter, you could probably do all of it in Inkscape; embedding raster images isn't a problem, although SVG is strictly-speaking a text format rather than an image format.

Pick whichever tool you like using. They're all flexible enough. You can probably do everything that you need to from the command line with ImageMagick, but I'm not sure why you'd want to :)

---

### Post by AlphaLexman on 2011-07-15
Follow these steps in [B]gimp.
[/B]
[LIST=1]
[*]File -> Open
[*]Select file for background
[*]Tools -> Text
[*]Insert (type) text
[*]Using mouse adjust boundaries as needed
[*]File -> Open as Layers
[*]Select file(s) for overlay
[*]Layer -> Layer to Boundary Size
[*]Adjust layer position as preferred
[*]File -> Save As
[*]Pick a unique filename
[*]File -> Print
[*]Sell your print, Makes lots of money !!
[*]Celebrate, send me royalties !!!!!!!!!!!!!
[*]You're Welcome.
[/LIST]

---

### Post by linuxuser12345 on 2011-07-15
I would suggest gLabels Label Designer, found in the Ubuntu Software Center

---

### Post by Syndicalist on 2011-07-16
Excellent suggestions here. Thank you everyone.

---

### Post by Syndicalist on 2011-07-21
What formats do you use in Inkscape?

I downloaded Glabels but I dont see it. Is it a plugin for something else?

---

### Post by CatKiller on 2011-07-22
> **Syndicalist said:**
> What formats do you use in Inkscape?

It uses SVGs, but I believe it can export to many different formats.

---

### Post by sanderd17 on 2011-07-22
> **CatKiller said:**
> It uses SVGs, but I believe it can export to many different formats.

SVG is the native format, but it works well (importing and exporting) with most other famous vector graphics like eps, pdf ... as well as with a lot of popular bitmap formats. Although you can get quality loss when you use bitmap pictures in inkscape.

---

### Post by CatKiller on 2011-07-22
It's not quality loss as such, it's that you lose the scalable nature of the image. You export at a particular resolution and the image is fixed at that resolution, as you'd expect.

An imported image is still fixed at its own resolution and changing its size doesn't look pretty. It doesn't have the advanced filtering tools that a dedicated raster graphics editor like the Gimp has.

---

### Post by mcduck on 2011-07-22
Gimp really isn't that great for print material, since it's a bitmap editor while quality print material requires graphics (an despecially any text) to be in some vector format instead.

Inkscape is a reasonable option, but I'd really recommend [Scribus]("http://www.scribus.net") if you need to create any print/press material.

---

### Post by Syndicalist on 2011-08-07
How do you add text in scribus? I like some of the features, especially for adding pictures where you want them.....GIMP needs to make that specific feature that easy....but otherwise its not that intuitive.

---

