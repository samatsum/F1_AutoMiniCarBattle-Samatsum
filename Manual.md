---

```markdown
# 🏎️ F1TENTH シミュレーター起動＆運転マニュアル（最終完成版）

このマニュアルは、キーボードの WASD で F1TENTH シミュレーターを操作するための最短手順です。
WSLのターミナルを **2つ** 開き、すべて `samatsum@DesktopSanshiro:~$` の状態からスタートします。

## 📺 ターミナル1：シミュレーター本体の起動

地図と車（Rviz）を表示します。

```bash
# 1. コンテナを起動（停止している場合に備えて）
docker start f1tenth_ros_dev

# 2. コンテナに入る
docker exec -it f1tenth_ros_dev bash

# 3. ワークスペースへ移動して設定を読み込む
cd /home/rosuser/catkin_ws
source devel/setup.bash

# 4. シミュレーターを起動
roslaunch f1tenth_simulator simulator.launch

```

> 👉 **確認**: Rviz画面（地図）が表示されます。このターミナルは**このまま放置**します。

---

##🎮 ターミナル2：コントローラーの起動操縦用のキーボードプログラムを起動します。

```bash
# 1. コンテナに入る
docker exec -it f1tenth_ros_dev bash

# 2. ワークスペースへ移動して設定を読み込む
cd /home/rosuser/catkin_ws
source devel/setup.bash

# 3. キーボード操縦プログラムを起動
rosrun f1tenth_simulator keyboard

```

> 👉 **確認**: "Reading from the keyboard..." と表示されれば準備完了です。

---

##🚦 運転開始の儀式1. **ターミナル2（コントローラー画面）** をクリックして選択状態にする。
2. **`K`** キーを押す。
* （ターミナル1のログに `Keyboard turned on` と表示されれば成功です）


3. **`W`** キーを長押しして発進！

| キー | 機能 |
| --- | --- |
| **W** | アクセル（前進） |
| **S** | ブレーキ / バック |
| **A** | 左ハンドル |
| **D** | 右ハンドル |

---

##🚑 事故った時の復活方法（リセット）壁に激突して `Collision detected`（衝突検知）となり動かなくなった場合：

1. **Rviz画面（地図）** の上部にある **緑色の矢印アイコン「2D Pose Estimate」** をクリック。
2. 地図上の**コースの中央（安全な場所）**で、マウスをドラッグ＆ドロップ。
* （車がその場所にワープし、衝突状態が解除されます）


3. 復活後、動かない場合は再度 **ターミナル2** で **`K`** を押してから運転再開。

```

```