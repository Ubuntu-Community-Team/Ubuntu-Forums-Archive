---
title: "Bash: how to use if statement for each line in file?"
date: 2010-05-15
forum: General Help
---

### Post by abcuser on 2010-05-15
Hi,
sample of my input_file.txt is:
```

cn: Albert
cn:: w5Z6bMO8Cg==

```

I would like to display above file according to two rules:
1. for each line that first column is "cn:", e.g. "cn: Albert", it should just display that row as it is written in file,
2. for each line that first column is "cn::" (notice two semicolons), e.g. "cn:: w5Z6bMO8Cg==", second column should be converted from base64 to ascii.

So output should be:
```

cn: Albert
cn:: Özlü

```

Little help:
To convert second column from base64 to ascii characters I use command:
```

gawk '/cn::/ {print $2}' input_file.txt | base64 -d

```
but I don't know how to use "if" statement for each line in file.

Thanks

---

### Post by abcuser on 2010-05-15
Hi,
I have managed to solve the problem with the following code.
```

#!/bin/bash
string=$(cat input_file.txt)
max_rows=$(echo "${string}" | gawk 'END { print NR }')
for (( i = 1; i <= ${max_rows}; i=i+1))
do
   line_by_line=$(echo "${string}" | gawk 'NR==count_i' count_i=$i)
   prefix=$(echo "${line_by_line}" | gawk '$1=="cn::" {print $1}')
   suffix=$(echo "${line_by_line}" | gawk '$1=="cn::" {print $2}')
   if [[ ${prefix} == "cn::" ]]; then
      ascii_string=$(echo ${suffix} | base64 -d)
      prefix_new=$(echo ${prefix} | sed 's/::/:/g')
      output_string="${prefix_new} ${ascii_string}"
   else
      output_string="${line_by_line}"
   fi
   echo "${output_string}"
done

```
Problem solved.
Thanks

---

