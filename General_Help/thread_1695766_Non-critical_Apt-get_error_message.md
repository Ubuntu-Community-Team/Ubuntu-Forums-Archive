---
title: "Non-critical Apt-get error message"
date: 2011-02-26
forum: General Help
---

### Post by Habeouscorpus on 2011-02-26
I get an odd error message sometimes when I perform an apt-get operation. 

```
 Processing triggers for shared-mime-info ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cactvs-ascii'

Unknown media type in type 'chemical/x-cactvs-binary'

Unknown media type in type 'chemical/x-cactvs-table'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-cdxml'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gamess-output'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-gulp'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-ncbi-asn1'

Unknown media type in type 'chemical/x-ncbi-asn1-binary'

Unknown media type in type 'chemical/x-ncbi-asn1-xml'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'

```

Everything works, and the task completes, but that's an odd message. I'd like to get rid of it if I could, or at least know what the heck's going on.

---

### Post by ajgreeny on 2011-02-26
Have you installed something from a ppa repository recently, or manually installed a .deb package with gdebi or software centre?

I occasionally get a similar error message in my terminal output after installing something, and simply re-installing the **gnome-mime-data** and **shared-mime-info** packages seems to get rid of the error.

Give it a try, and tell me if it works;  I'll be very interested to hear!

---

### Post by Habeouscorpus on 2011-02-26
I reinstalled, I'll see if it works! Thank you. 

(It doesn't happen with every apt-get operation, just some. Hopefully it won't happen again!)

---

