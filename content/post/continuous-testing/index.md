---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Enterprise Continuous Testing in 1500 words"
subtitle: "This article was inspired by [“Enterprise Continuous Testing”](https://www.amazon.com/Enterprise-Continuous-Testing-Transforming-DevOps/dp/1699022941) book by [Cynthia Dunlop](https://medium.com/@cynthiadunlop) and [Wolfgang Platz](https://www.linkedin.com/in/wolfgang-platz-2a68681b/). Yes, I bought it 🙂. Honestly, I’m quite skeptical about reading books on technologies. I think books are slow. We have plenty of information sources today which are easier to access, more responsive to changes and sometimes even free.


However, this book is exceptional. It’s conceptual and that’s why it will not become outdated tomorrow. After reading it, I tried to put together my own thoughts on Continuous Testing. Some of them are flavored by ideas I read. Dive in ⮯"
summary: "I tried to put together my own thoughts on Continuous Testing. Some of them are flavored by ideas I read."
authors: [admin]
tags: ["continuous testing"]
categories: ["medium"]
date: 2022-01-15T23:31:18+03:00
lastmod: 2022-01-15T23:31:18+03:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

## Testing doesn’t create added value?

Well, yes. And even more — it is source of spending. In ideal world with rainbows, unicorns nibbling grass and people not making mistakes testing is probably excessive. But in our universe, it is essential and often expensive. What would you do with something annoying though necessary to do? Right! Ask someone else to do it 🙂. This is exactly what was happening when companies sought to outsource testing.

As a result, testing was just another phase in waterfall process. It was pretty much detached activity which provides delayed feedback, and the entire process was as transparent as smoking room at the airport.

Quality as source for decision making
Can you answer this question: “Is your latest build ready to be promoted to production right now?”. If your answer is “Yes”, then you may want to skip reading rest of the story. If your answer is “No”, that’s not that bad! But if you are not sure, then your testing process maturity is likely at opportunistic level.

Yes, Continuous Testing is all about making business decisions based on current data on quality. At the end of the day, businesses are not too concerned about coverage, test results, and even quality. They operate such concepts as time to market and business risk. So, what can help to make decisions based on quality at any given moment?

## Pillars of Continuous Testing
Continuous Testing lays down on both processes and technologies. Automated Testing is a foundation, most critical activity, yet a part of the puzzle.

### 01 Risk-based automated testing
Traditionally, high Test Automation coverage has been considered as a key indicator of testing maturity. However, automated tests bring quick value only when the number of tests is relatively small. When this number reaches thousand, complexity grows, and testing slows down again. Teams receive late feedback not because of high manual effort but because of increased effort to implement, maintain and analyze tons of automation artifacts.

While there are different smart approaches which can facilitate managing high number of automation assets, risk-based test coverage is the most deliberate step towards Continuous Testing at a large scale.

In short, risk-based approach relies on:
- identifying risks for functional areas;
- risk assessment based on probability and consequences;
- detecting and eliminating not tested areas or areas with not measured risk;
- maximizing coverage for business functionality with higher risk exposure;
- prioritization of tests based on risk analysis;
- test failure analysis based on risk exposure.

The procedure of risk definition and analysis is very well explained in “Enterprise Continuous Testing” book. Understanding what percentage of your business risk is covered by test cases and potential impact of failures gives ability to make well-grounded decisions based on current build quality.

### 02 Hard quality gates in automated delivery pipeline

Having prioritized automated test suite is not 100% of success. Next step is to make automation work and serve the goal of delivering quickly and with high quality.

I heard these words from development teams: “We are afraid to break pipeline”. But it’s… pointless. Break it! And then fix it. All the tests are created specifically for this purpose — to hard-stop delivery pipeline before broken functionality hits end users. I suggest considering quality gate as emergency break which is triggered automatically before the train crashes. Better sooner than later.

This is the minimal list of quality gates I’d recommend to include in delivery pipeline:
- Static code analysis;
- Unit tests;
- Integration tests;
- API end-to-end tests;
- UI system tests.

They are listed in the order of feedback speed and potential impact of failure. It doesn’t make much sense to spend time on executing time-consuming UI system tests if there are failures on lowers levels. This is the whole idea of hard quality gates — zero tolerance to failures on each level. It can take significant effort to fix all failures in the beginning if you did not set up quality gates on initial stage of product development. But as soon as you do this, your maintenance and analysis effort will drop significantly. However, you might want to proceed with deploying a build to upper environments if test failures concentrate in low priority functional areas. You can achieve this by configuring quality gates so that pipeline stops only when the percentage of business risk that seems to be broken exceeds threshold.

### 03 Quick and effective analysis of test results

Standard target for percentage of passed tests is 90% and more. The higher pass rate you have, the faster decisions you can take. However, time for analysis and investigating failures is crucial factor for quick feedback. If test stability is close to 95% but it takes days to do root cause analysis for 5% failures, this doesn’t help to make decisions faster.

The good news is that the power of AI and ML technologies nowadays can save tons of time and effort for results analysis. It is a good idea to give a try to Report Portal or other test reporting tools. They can help to do quick and smart results analysis on a large scale. Killing feature of such tools is automatic classification of failures so that you always see if your tests fail due to product defect, infrastructure problem or bug in test.

### 04 Up to date dashboards with Quality Metrics

Single source of truth for product quality is crucial for Continuous Testing enablement. But no hurry to develop shared excel sheets with numbers and charts. There are out-of-the-box solutions for this. Test reporting tools can not only classify test failures but also visualize test results and calculate test execution statistics based on them.

However, their capabilities may be limited to track all product-wise quality metrics such as Defect Containment Efficiency or Defect Density. Some tools like Azure DevOps allow to collect and visualize all necessary metrics in one place. So that you can build comprehensive and customized dashboards which are always accessible to the team and stakeholders.

Another option is to collect all your data including test cases, defects, test results in single storage and use Power BI or alternative tools for data processing and visualization. This approach required higher initial investments but gives maximum flexibility. Whatever tool you choose, critical criteria for metric dashboard are ease of access, relevance and support for multiple teams and projects.

### 05 Non-functional tests in pipeline

It happens quite often when companies invest disproportionately big effort into functional validation while non-functional testing is ignored or postponed prior to release date.

Level of automation for non-functional tests is traditionally lower than that for functional tests. From other side, no matter how quick feedback from functional validation is if performance and security tests take long time to prepare, run and process results prior to release. And there are more non-functional tests which may be applicable for you project including accessibility, availability, resiliency, usability tests.

While some of them are automated by their nature, others may require significant efforts for integrating them in delivery pipeline. Automate as much as you can, execute the rest manually but repeatedly. There are tools which facilitate implementation of non-functional quality gates in pipeline as well. You may want to give them a try.

### 06 Manual effort limited to exploratory testing

Now, what to do with manual regression which always exists at some extent. I have simple solution — get rid of it and see what happens. Seriously. However, it should be controlled experiment. Analyze how many regression defects does team find during manual testing cycle and what are their priorities. It may occur that long repeatable manual testing doesn’t really help to find severe errors.

Exploratory and ad hock testing can be even more efficient allowing team to discover non-trivial yet severe product issues during such time-boxed activity. If this is crucial to have visual testing, there are several automated solutions on the market like Applitools. In short, if it is vital to run manual tests, run them but limit in time and concentrate on areas with higher business risk. Monitor testing efficiency and adjust test strategy as soon as you see quality dropped.

## Full control over failures

And finally, nothing’s perfect. And nothing gives you more confidence than a reliable backup. Automated deployment to production is a great thing. Automated rollback is even better. 🙂

***

Keep reading on [Medium](https://medium.com/@pavel.makhakhei)
