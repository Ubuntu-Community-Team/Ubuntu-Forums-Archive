---
title: "How to filter data with criteria J_min &lt; J &lt; J_max in GnuMeric ?"
date: 2011-05-21
forum: General Help
---

### Post by Jacare Omoplata on 2011-05-21
Hi, 

I'm new to GnuMeric. I've searched but can't find the answer anywhere. 

I have a set of rows with a column named 'J'. I want to apply a filter with criterea 14.4 < J < 16. 

Here's what I tried to do. 
*Copied the heading row and pasted below the data set. 
*In the cell below 'J', typed '>14.4', and in the cell below that, typed '<16'. 
*Chose 'Advanced Filter..' from the menu 'Data -> Filter', and  entered the data set as the 'List range', and entered the three cells  under (and including) the column 'J' pasted below the data set as the  'Criterea range'. 
But I get all of the dataset as the filter result. It seems to me  that GnuMeric interprets my criterea as '(J > 14.4) OR (J < 16)'. 
But what I want is '(J > 14.4) AND (J < 16)'. How do I do this? 

Thanks.

---

