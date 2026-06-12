---
title: "Image batch conversion for publishing"
date: 2011-05-27
forum: General Help
---

### Post by orodoni_le on 2011-05-27
I have a LaTeX document in one folder, and the images that this documents includes via
```
\includegraphics{filename}
```
are in subfolders of this directory. Sometimes I compile this LaTeX file using PDFLaTeX, and others using plain LaTeX. Thus, I would like to have my images in PDF and EPS format, along with its original source, normally an SVG file created with Inkscape. I know I can use Inkscape to convert these files to these formats, but when there are 50 images, it becomes cumbersome/boring/APITA.

I have a small Makefile that reads gnuplot scripts and generates EPS files

```

# Makefile to convert into Encapsulated Postscript
# the plots made with GNU Plot. (.plt files)

.PHONY=eps,clean

PLOTS=$(shell ls *.plt 2> /dev/null)

%.eps : %.gp
	@gnuplot $<

eps: $(PLOTS:.plt=.eps)

clean:
	@rm -f $(PLOTS:.plt=.eps) *~

```

I also know than Inkscape converts, via command line. For example, I use
```
inkscape -D -T -E foo.eps -A foo.pdf foo.svg

```

And it reads the foo.svg file, and creates a foo.pdf and a foo.eps file afterwards. The -D and -T are for output formatting, -D:export drawing, -T:text to paths.

I wonder if there's a way to include a similar command in a Makefile, just like the one in GNU Plot, and being able to convert in batch, via Inkscape. My problem is the filename, with the extension. Not sure hoy to pass them in the Makefile

---

### Post by orodoni_le on 2011-05-27
I did something like this. The results are far from perfect

```

# Makefile to convert into Encapsulated Postscript
# the plots made with Inkscape. (.svg files)

.PHONY=eps,clean

IMAGES=$(shell ls *.svg 2> /dev/null)

%.eps : %.svg
	@inkscape -D -T -E $<.eps -A $<.pdf $<

eps: $(IMAGES:.svg=.eps)

clean:
	@rm -f $(IMAGES:.svg=.eps) *~

```

At the end, it produces "filename.svg.pdf" and "filename.svg.eps". I tried to create the list in the makefile using find insteas of ls
```
IMAGES=$(shell find . -name '*.svg' | sed 's/.\///g' | sed 's/.svg//g' 2> /dev/null)

```

But it gives an error:
```
make: *** No rule to make target `filename', needed by `eps'.  Stop.
```

---

### Post by orodoni_le on 2011-05-27
Solved.

This is my Makefile

```

# Makefile to convert into Encapsulated Postscript
# the images made with Inkscape. (.svg files)

.PHONY=eps,clean

IMAGES=$(shell find . -name '*.svg' | sed 's/.\///g' | sed 's/.svg//g' 2> /dev/null)

%.eps : %.svg
	@inkscape -D -T -E $(<:.svg=.eps) -f $<
	@inkscape -D -T -A $(<:.svg=.pdf) -f $<


eps: $(IMAGES:=.eps)

clean:
	@find -maxdepth 1 -type f -regex '.*\(eps\|pdf\)' -printf %f\  -delete
	@echo "\f"

```

I know it's not standard. It should be an "all:" section, instead of the "eps:" one, because I'm building both the eps and the pdf there. But it works for me.

---

### Post by program404 on 2012-07-17
Thank you for your post, I had been looking for a solution for some time. I can add that your solution can be restated a bit shorter. My code does .eps to .pdf conversion. Cheers.


```
# Makefile for batch conversion of .eps to .pdf

IMAGES=${patsubst %.eps,%.pdf,${wildcard *.eps}}

%.pdf : %.eps
    epstopdf $< -o $@

pdf: $(IMAGES)
```

---

