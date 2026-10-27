# alertthresh

**从历史数据推导告警阈值。**

`alertthresh` —— 用分位数与异常检测方法给出阈值建议，并估算误报频率

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`alertthresh.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install sunnycrowd-alertthresh
```

装完直接用命令名调用：

```bash
alertthresh --help
```

也可以不用安装，直接把 `alertthresh.py` 拷走用——它只依赖标准库。

## 为什么需要它

阈值要附带误报预期，否则调完还是会被淹没

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 告警阈值推导 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python alertthresh.py --file input.txt
python alertthresh.py --text "示例内容"
python alertthresh.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 分箱是等宽或等频，样本太少时结论不稳。
- 不做显著性检验。

## 跑测试

```bash
python test_alertthresh.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/sunnycrowd/alertthresh>

---

## 关于作者

sunnycrowd 做告警阈值推导相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://sunnycrowd.github.io>
- 仓库：<https://github.com/sunnycrowd/alertthresh>

## 许可

MIT，见 [LICENSE](LICENSE)。
