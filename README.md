# Readme
import sys  # 导入sys包


# 获取文件路径，文件为第二个参数，第一个参数为脚本
input_file = sys.argv[1]
# 使用with方式打开文件，文件使用完后自动关闭
with open(input_file, 'r',  encoding="utf-8") as f:
    data = f.read()
    str1 = data.split("\n")
    # print(str1)
    # print(type(str1))
    list1 = []
    for temp in str1:  # 将所有数据划分为一个二维数组
        x = temp.split("\t")
        list1.append(x)
    # print(list1)


output_file = sys.argv[2]
temp = list1[0][0]  # 暂存第一个省份，用于后面的判断


with open(output_file, 'w+',  encoding="utf-8") as f:
    f.write(temp + "\n")
    # print(temp + "\n")
    for x in list1:
        if len(x) != 1:  # 避免列表中一个不知名的空列表（其长度为一）
            province = x[0]
            if province != temp:
                temp = province
                f.write("\n" + temp + "\n")
            f.write(x[1] + "\t" + x[2] + "\n")

