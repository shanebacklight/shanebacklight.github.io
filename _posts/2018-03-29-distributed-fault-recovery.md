---
layout:     post
title:      Distributed Fault Recovery
date:       2018-03-29 20:00:00
author:     "Shane"
header-img: "img/bg-mac.jpg"
catalog: true
tags:
    - Note
    - Distributed System
---

> Prove the consistency of checkpoint algorithm by contradiction.

Please read slides on fault recovery alogrithm prepare by Prof. Gagan first.

![](https://i.imgur.com/SkYA9dr.jpg)

**Claim:** Orphan messages are not acceptable by this algorihm.
**Proof:** <br>
Assume an orphan message *M* exit between thread **Y** and **Z**. Without the loss of generality, consider Z as the sender and Y as the receiver. By definition of orphan message, *M* must be sent after t3 and received before t2. By the checkpoint algorithm, no message is allowed to sent at the interval between tentative point and commit point. Thus, *M* could only be sent after t5. In other words, t_5 < t_6 and t_7 < t_2.

By checkpoint algorithm, we could obtain the conclusion t_2 < t_4 < t_5. Revisit the relations at the end of above paragragh, the final time chain would be t_7 < t_6.

Contradiction: The sending time is larger than the receiving time! 