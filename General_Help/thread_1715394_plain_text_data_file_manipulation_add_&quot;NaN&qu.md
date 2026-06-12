---
title: "plain text data file manipulation: add &quot;NaN&quot; to empty entries"
date: 2011-03-26
forum: General Help
---

### Post by lethalfang on 2011-03-26
Hey, guys, say if I have a file that looks like this:

```
1	.143	.165	-.211	.272	.046	.429	.183
2	.111	.101	-.14	.237	-.109	.149	.252
3	.072	.15	.115	.469	-.015	.144	.215
4	-2.392	-1.193			-.963	-.51	-.939
5	-1.277	-.741	-.194	.227	-.986	-.048	
6	.404	-.351	.32	.425	-.574	-.522	.249
7	-.659	.272	-.009	.825	.544	.353	.545
8	-.246	-.131	.478	1.699	-.026	.365	.435
9					-.688	.008	
10	-.427				-3.841	.312	0
```


Clearly, there are some empty spots. How do I fill them up with "NaN" (so that it can be read by MATLAB), so that it looks like this?


```
1	.143	.165	-.211	.272	.046	.429	.183
2	.111	.101	-.14	.237	-.109	.149	.252
3	.072	.15	.115	.469	-.015	.144	.215
4	-2.392	-1.193	NaN	NaN	-.963	-.51	-.939
5	-1.277	-.741	-.194	.227	-.986	-.048	NaN
6	.404	-.351	.32	.425	-.574	-.522	.249
7	-.659	.272	-.009	.825	.544	.353	.545
8	-.246	-.131	.478	1.699	-.026	.365	.435
9	NaN	NaN	NaN	NaN	-.688	.008	NaN
10	-.427	NaN	NaN	NaN	-3.841	.312	0



```

Thanks.

---

