---
title: "bash sort and -d option"
date: 2012-01-13
forum: General Help
---

### Post by engine on 2012-01-13
Just spent longer than expected producing a sorted list of unique tags from an MML file, where tags are marked off with <: and >

It looks to me as though the sort command is running as sort -d, which is not what I need.
[LIST]
[*]has sort been tweaked
[*]if so, how do I override the -d switch
[/LIST]

Thanks in advance!

---

### Post by Lars Noodén on 2012-01-13
Can you post a few lines of data illustrating the problem you are getting and the results you would like to have instead?

---

### Post by engine on 2012-01-17
Thanks! Here's what I'm getting ...
```

<:a1>
<:anchor>
Area of land, part of a facility.
Basic division of a land parcel; generally used to identify different land usage within a parcel.
<:contents>
<:dd>
Defined area usually made up of one or more land parcels.
<:dt>
Facility
<:h1_n>
<:h2_n>
<:h3_n>
<:icon>
Information recorded for each facility includes name and location code.
Information recorded for each parcel includes legal description and physical characteristics.
<:list_2>
<:lp>
Note that there is no direct relationship between a sub-parcel and a building.
<:ol>
<:ol_alpha>
<:p>
<:p_icon>
Parcel
Parcels can be divided into sub-parcels, and can contain one or more buildings.
Sub-parcel

```
and here's what I'd expected
```

<:a1>
<:anchor>
<:contents>
<:dd>
<:dt>
<:h1_n>
<:h2_n>
<:h3_n>
<:icon>
<:list_2>
<:lp>
<:ol>
<:ol_alpha>
<:p>
<:p_icon>
Area of land, part of a facility.
Basic division of a land parcel; generally used to identify different land usage within a parcel.
Defined area usually made up of one or more land parcels.
Facility
Information recorded for each facility includes name and location code.
Information recorded for each parcel includes legal description and physical characteristics.
Note that there is no direct relationship between a sub-parcel and a building.
Parcel
Parcels can be divided into sub-parcels, and can contain one or more buildings.
Sub-parcel

```
I have seen it suggested that ubuntu uses "GNU sort", if that's relevant …

---

