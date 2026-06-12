---
title: "Syntax issues in computing average with parsed data"
date: 2011-02-17
forum: General Help
---

### Post by jmadsen on 2011-02-17
I am working on a script that reads a data file and computes the average flux if there are 4 consecutive cell id's that match up but I am having syntax error in my IF statement in the computing the average statement.

Here is the part of script that is having the issues:

    IFS=" "
    while read cell_id element_id group flux
    do
      c_prev3=$c_prev2
      c_prev2=$c_prev1      
      c_prev1=$c_var
      c_var=$cell_id
      g_prev3=$g_prev2
      g_prev2=$g_prev1      
      g_prev1=$g_var
      g_var=$group
      f_prev3=$f_prev2
      f_prev2=$f_prev1      
      f_prev1=$f_var
      f_var=$flux
      if (($c_var==$c_prev1)) && (($c_var==$c_prev2)) && (($c_prev2==$c_prev3))
      then
	 flux_avg=$(( (($f_var+$f_prev1+$f_prev2+$f_prev3)) /4))
	 echo $c_var" "$g_var" "$f_var
      fi
    done<./element_file.group.sorted


here is the error in the output:

./NEW_GREP_SEARCH.sh: line 74: ((: 2646==: syntax error: operand expected (error token is "=")
2988 0 0
3006 0 0
3024 0 0
3042 0 0
3312 0 0
3330 0 0
3348 0 0
3366 0 0
3636 0 0
3654 0 0
3672 0 0
3690 0 0
3960 0 0
3978 0 0
3996 0 0
4014 0 0
4284 0 0
4302 0 0
4320 0 0
4338 0 0
4608 0 0
4626 0 0
4644 0 0
4662 0 0
./NEW_GREP_SEARCH.sh: line 76: ((0.221472728291055+-1.89082223551397+0.379311153658852+0.0229668139977545)) /4: missing `)' (error token is ".221472728291055+-1.89082223551397+0.379311153658852+0.0229668139977545)) /4")


The script seems to work for the inputs with three columns (e.g. 2988 0 0) but appears to fail when dealing with non-integers.

---

