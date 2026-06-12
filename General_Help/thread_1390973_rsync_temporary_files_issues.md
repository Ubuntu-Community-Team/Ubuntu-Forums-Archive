---
title: "rsync temporary files issues"
date: 2010-01-26
forum: General Help
---

### Post by !nkubus on 2010-01-26
I had a small issue with a webserver being very slow, and my rsync script created a bunch a of temporary files because 1st rsync didn't finished, but the problem was just getting bigger as the number of temporary files was growing exponatially it went to a point where 20 rsync instances were running at the same time.

the files have a special pattern:
```

 f8fe85f535c820608fb2e89c682613e7.pdf
-rw------- 1 bsw-jpr bsw-jpr   8192 Jan 26 08:03 .f8fe85f535c820608fb2e89c682613e7.pdf.6p5ZJR
-rw------- 1 bsw-jpr bsw-jpr   8192 Jan 26 08:03 ..f8fe85f535c820608fb2e89c682613e7.pdf.6p5ZJR.FsHcec
-rw------- 1 bsw-jpr bsw-jpr   8192 Jan 26 08:03 ...f8fe85f535c820608fb2e89c682613e7.pdf.6p5ZJR.FsHcec.dV9zGZ


```

as you can see there a . is added at each transfer in front of the file and 6 characters at the end of each temporary file.

I have yet to find how to remove all theses temp files recursively on the webserver without rewmoving the real files in this case(f8fe85f535c820608fb2e89c682613e7.pdf). because I have over 20k temporary files in 100 folders to remove, I want to avoid going in each folder and remove them manually.

Any quick help would be appreciated :)

Thanks

---

