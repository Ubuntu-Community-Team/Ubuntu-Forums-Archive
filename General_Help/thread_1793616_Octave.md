---
title: "Octave"
date: 2011-06-29
forum: General Help
---

### Post by bredsj on 2011-06-29
I want to read data from a spreadsheet into Octave with the following code:

[INDENT]% get a pointer for reading from spreadsheet
ods1 = odsopen ('Protocol.ods',[],'JOD');
          
% read the data
A = ods2oct (ods1, 'Data', 'C21:J21');

% Close spreadsheet file pointed to in pointer struct ods1; 
% ods1 is reset
ods1 = odsclose (ods1);[/INDENT]

There are two supported interfaces: OTK and JOD. I can't get either to work.

Is there anybody with experience in this regard that can help me? It would be very much appreciated.

---

