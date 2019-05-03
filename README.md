# AfreecaTVCrawler

~~*考虑到 AfreecaTV 的带宽质量堪忧，此脚本下载的视频几乎不可避免会出现片段丢失情况，因此不推荐使用。*~~

~~目前主要问题还是目标站点的服务器不断抛出 500 Internal Server Error 错误，这往往是 AfreecaTV 内部服务器错误而不是爬虫本身的问题，但是意味着大量 ts 文件会获取失败，用 wget 方法重复下载无法解决此问题。~~
~~目前新的思路是通过传统的 requests.get(url).content 方法获取 ts 文件，在遇到错误后它会获取到一个 800K 左右的非正常文件，而正常的 ts 文件大小为 2M 左右，故通过比较文件大小可以确定是否需要反复下载失败的文件。~~

已经加入 gevent 并发协程，下载功能基本可用，经测试，3000 个分片组成的直播下载后丢失的 ts 分片可以控制在 20 个以内。此后的脚本将不再需要借助东亚地区（日韩） VPS 加速，中国大陆可以直接下载（需使用代理，具体如何设置请参考其他教程）。

功能仍在完善中，任何问题请提 issue。

