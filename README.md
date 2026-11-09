# Macau medium-voltage test case / 澳门中压算例

1,641 nodes (25 sources and 1,616 aggregated loads), 308 feeders and 1,768 lines (1,616 in service and 152 open ties).

1,641 个节点（25 个电源、1,616 个聚合负荷）、308 条馈线、1,768 条线路（1,616 条投入、152 条常开联络线）。

## nodes.csv / 节点

| Field | Meaning / 含义 |
|---|---|
| `node_id` | Node ID / 节点编号 |
| `node_type` | `S`: source; `T`: aggregated MV load / `S`：电源；`T`：中压侧聚合负荷 |
| `longitude` | Longitude (°) / 经度（°） |
| `latitude` | Latitude (°) / 纬度（°） |
| `load_kw` | Active demand in kW; positive means consumption / 有功负荷，单位：kW；正值表示消耗 |
| `feeder_id` | Base feeder ID; blank for sources / 基准馈线编号；电源节点留空 |

## lines.csv / 线路

| Field | Meaning / 含义 |
|---|---|
| `from_node` | First endpoint, referring to `node_id` / 一端节点，对应 `node_id` |
| `to_node` | Second endpoint, referring to `node_id` / 另一端节点，对应 `node_id` |
| `length_m` | Routed line length (m) / 线路路径长度（m） |
| `base_status` | Base configuration: `1` in service, `0` open / 基准方式：`1` 投入，`0` 断开 |

## Power-flow parameters / 潮流计算参数

Balanced three-phase model: nominal voltage 10 kV, system base 10 MVA, frequency 50 Hz; source voltage 1.0 pu at 0°; load power factor 0.95 lagging, Q = P × tan(arccos(0.95)). All lines use R = 0.16 Ω/km, X = 0.11 Ω/km, C = 0.39 nF/km and rated current 0.5 kA.

三相平衡模型：额定电压 10 kV、系统基准容量 10 MVA、频率 50 Hz；电源电压 1.0 pu、相角 0°；负荷功率因数 0.95（感性），Q = P × tan(arccos(0.95))。线路统一采用 R = 0.16 Ω/km、X = 0.11 Ω/km、C = 0.39 nF/km，额定电流 0.5 kA。
