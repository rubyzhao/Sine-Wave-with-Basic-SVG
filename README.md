## Manually Performace test results using performance.getEntries() from console of Chrome

This is further investigation for [Big different window.performance.timing results for repeat test on the same page](https://github.com/GoogleChrome/puppeteer/issues/5110)

For each **Loop**=20,200 and 2000, refresh the website http://127.0.0.1:5500/SVG_Sin.html, run JSON.stringify(performance.getEntries()) and save as the result in the conslole a few times. 

The below is part of performance result for Loop=20:

NAV_duration | NAV_connectEnd | NAV_responseEnd | NAV_domContentLoadedEventEnd | NAV_domComplete | FP_startTime | LogFileTime
---|---|---|---|---|---|---
122.8 | 0.9 | 7.0 | 49.6 | 122.3 | 52.7 | 03-11-2019-11-34-35
128.1 | 0.9 | 16.7 | 65.5 | 127.4 | 69.3 | 03-11-2019-11-34-55
140.9 | 0.9 | 16.6 | 64.7 | 140.3 | 67.9 | 03-11-2019-11-35-30

The below is part of performance result for Loop=200:

NAV_duration | NAV_connectEnd | NAV_responseEnd | NAV_domContentLoadedEventEnd | NAV_domComplete | FP_startTime | LogFileTime
---|---|---|---|---|---|---
161.8 | 3.9 | 38.1 | 120.6 | 160.8 | 100.5 | 03-11-2019-11-12-15
138.5 | 1.1 | 17.3 | 64.5 | 137.7 | 72.8 | 03-11-2019-11-12-32
153.0 | 1.0 | 17.2 | 71.5 | 151.9 | 77.4 | 03-11-2019-11-12-49
135.0 | 1.3 | 12.7 | 70.3 | 134.5 | 77.5 | 03-11-2019-11-32-42

The below is part of performance result for Loop=2000:

NAV_duration | NAV_connectEnd | NAV_responseEnd | NAV_domContentLoadedEventEnd | NAV_domComplete | FP_startTime | LogFileTime
---|---|---|---|---|---|---
241.9 | 0.7 | 23.1 | 140.3 | 240.6 | 172.06 | 03-11-2019-10-12-03
252.6 | 1.2 | 20.5 | 152.2 | 251.6 | 178.86 | 03-11-2019-10-16-31
250.6 | 0.8 | 18.2 | 151.3 | 249.8 | 182.095 | 03-11-2019-11-08-26

The variance is big. For example, NAV_domComplete=140.3 at Loop=20 is even higher than 137.7 and 134.5 in Loop=200.

### Environment ###
- Live Server: v5.6.1
- Chrome: Version 78.0.3904.87 (Official Build) (64-bit)
- Windows: W10X64 1803
- Node.js version: v12.11.1

