---
title: "Software catalog"
date: 2011-06-25
forum: General Help
---

### Post by Spritegeezer on 2011-06-25
Is there a catalog of available applications available that is searchable by subject matter?  I know about Synaptic and Ubuntu center.  I'm looking for sources of more specialized applications like multi-variant ANOVA analysis or other such statistical packages.  It can sometimes be quite difficult to determine exactly what a package is used for from its name.  Sometimes the authors get too cute by half in naming them.;)

---

### Post by mike555 on 2011-06-25
Try using;    [http://www.googlubuntu.com/](http://www.googlubuntu.com/)   , it would give more Ubuntu related results than regular Google.

---

### Post by Cheesehead on 2011-06-25
Try the 'apt-cache search <foo>' and 'apt-cache show <packagename>' commands.

For example (using 10.10),
```
bot:~$ apt-cache search anova       # No match for the search term
bot:~$ apt-cache search variance    # So let's try something more general
                             # Returns a list of package names
cstream - general-purpose stream-handling tool similar to dd
infernal - inference of RNA secondary structural alignments
infernal-doc - inference of RNA secondary structural alignments – documentation
libcommons-math-java - Java lightweight mathematics and statistics components
libcommons-math-java-doc - Java lightweight mathematics and statistics components - documentation
libdiagnostics-dev - Logging, unittesting, and runtime diagnostics for C++ - development files
libdiagnostics0 - Logging, unittesting, and runtime diagnostics for C++ - library
libstatistics-basic-perl - collection of very basic statistics modules
octave-statistics - additional statistical functions for Octave
python-stats - A collection of statistical functions for Python
r-other-mott-happy - GNU R package for fine-mapping complex diseases
ttf-aenigma - 465 free TrueType fonts by Brian Kent

bot:~$ apt-cache show python-stats    # Let's take a look at a promising package
Package: python-stats
[...edit...]
Description: A collection of statistical functions for Python
 Python-stats provides a collection of statistical functions for Python.
 These functions can be applied to Python lists, Python tuples, and
 Numeric arrays.   Most common statistical functions such as mean,
 standard deviation, median, mode, skewness, kurtosis, etc., are provided,
 along with functions for statistical hypothesis testing, analysis of
 variance, and for computing probability distribution functions.
Homepage: http://www.nmr.mgh.harvard.edu/Neural_Systems_Group/gary/python.html
Python-Version: all

bot:~$ 
```

There is no 'catalog' beyond each package's Description field. Happily, you already have all those in your apt cache already. And those commands are one of the best ways to search them.

---

