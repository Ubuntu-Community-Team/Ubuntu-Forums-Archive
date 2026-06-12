---
title: "C++ fstream open failed"
date: 2012-03-13
forum: General Help
---

### Post by mzimmers on 2012-03-13
I hope this is the right forum for this. I would like to port a program that currently runs on Mac OS X and a couple flavors of Windows. The program built successfully, but failed here:

[HTML]	filename = "config/coeff_nyquist_2048.dat";
	fp_nyquist.open(filename.c_str(), fstream::in);
	if (!fp_nyquist.good()) {
		cout << "Error: Can't open file " << filename << endl ;
		return -1;
	}
[/HTML]

Any ideas?

EDIT: please disregard; this was cockpit error. I'm using Qt, and I forgot to set the working directory for the program. It seems fine now.

---

