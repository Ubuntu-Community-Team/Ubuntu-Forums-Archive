---
title: "PDFTK: &quot;fill_form&quot; not filling in the form"
date: 2010-10-13
forum: General Help
---

### Post by lemursfemur on 2010-10-13
Running the following pdftk command from the command line fails to fill out the form. It only returns the example.pdf with no form data from the fdf file inserted. Even though the fdf file HAS new form data.

1) All files permissions are set to 777
2) It is successful OUTPUTTING the form data when using 
passthru('/usr/bin/pdftk example.pdf fill_form fdfzu1zfG.fdf output out.pdf flatten'); 
in a php script. But I want to save it to the server. (I'll use exec() once I can get it working from the command line).

[PHP]

me@ubuntu:/home/$ /usr/bin/pdftk example.pdf fill_form fdfzu1zfG.fdf output out.pdf flatten

me@ubuntu:/home/$ pdftk example.pdf dump_data_fields
---
FieldType: Text
FieldName: firstname
FieldFlags: 0
FieldJustification: Left
---
FieldType: Text
FieldName: lastname
FieldFlags: 0
FieldJustification: Left
[/PHP]

The fdfzu1zfG.fdf looks like .... (note the form field names correspond with those in example.pdf)
[PHP]
%FDF-1.2
%&#65533;&#65533;&#65533;&#65533;
1 0 obj
<< 
/FDF << /Fields [ << /T (firstname) /V (ted) /ClrF 2 /ClrFf 1 >> 
<< /T (lastname) /V (Beaver) /ClrF 2 /ClrFf 1 >> 
] 
>> 
>> 
endobj
trailer
<<
/Root 1 0 R 

>>
%%EOF
[/PHP]Any suggestions?

Thanks

Ubuntu 9.04 Jaunty

---

### Post by lemursfemur on 2010-10-14
bump

---

