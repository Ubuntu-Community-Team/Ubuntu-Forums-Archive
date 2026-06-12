---
title: "Okular does't display the entire Document"
date: 2012-05-12
forum: General Help
---

### Post by 1991sudarshan on 2012-05-12
I am using Kubuntu 10.04. I notice this bug with Okular. Okular doesn't display the document fully written in Japan rather just shows the scattered Japanese character. But the same file opens pproperly in windows xp. What is the probable solution for this bug?

I have posted the screen shots of the Japanese pdf file in the Okular and the same document in the Google Doc.

---

### Post by 1991sudarshan on 2012-09-09
> **1991sudarshan said:**
> I am using Kubuntu 10.04. I notice this bug with Okular. Okular doesn't display the document fully written in Japan rather just shows the scattered Japanese character. But the same file opens pproperly in windows xp. What is the probable solution for this bug?

I have posted the screen shots of the Japanese pdf file in the Okular and the same document in the Google Doc.

Found out the solution. 

Previously the package poppler-data was not installed. Due to that, the Japanese font in the pdf were not displayed properly 

```
sudo apt-get install poppler-data 
```

---

