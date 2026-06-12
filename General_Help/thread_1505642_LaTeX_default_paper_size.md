---
title: "LaTeX default paper size"
date: 2010-06-09
forum: General Help
---

### Post by rplantz on 2010-06-09
I'm using texlive on Lucid. I have used texlive on previous releases for several years.

I use the geometry package to create a smaller print page size on letter (8.5 X 11) physical paper for a book.

The first thing I found is that the default paper size in Lucid's texlive is a4 instead of letter. So I have to use the "-t letter" option to dvips.

With
```

\usepackage[paperwidth=7.44in,paperheight=11.0in,
        textwidth=6.0in,marginparwidth=1.0in,
          top=1.0in,bottom=1.0in,centering]{geometry}

```
the printed page is narrower than and centered on the physical page. Exactly what one would expect.

However, if I do
```

\usepackage[paperwidth=7.44in,paperheight=9.68in,
        textwidth=6.0in,marginparwidth=1.0in,
          top=1.0in,bottom=1.0in,centering]{geometry}

```
the printed page is centered right to left, but not from top to bottom. It is about 2 inches from the top, and the bottom of the printed page spills off the bottom of the physical page. How can I fix this?

This all worked fine on previous Ubuntu releases.

---

### Post by kirillt on 2012-01-05
The following worked for me:

```
sudo texconfig paper letter
```

Also, man texconfig.

---

