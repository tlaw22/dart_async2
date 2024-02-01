A sample command-line application with an entrypoint in `bin/`, library code
in `lib/`, and example unit test in `test/`.

```Dart
void main(List<String> arguments) async {
  String studentName = '';
  print("Begin operation...");
  showResult();
  print("Processing...");
  print("Complete!");
  print("=============================");

  getStudentName(3).then((Map value) {
    // print(value);
    // studentName = value['studentName'];
    getCourseInfo(value['studentName']).then((value) {
      print(value);
      String courseName = value[0];
      getGrade(courseName).then((value) {
        print(value);
      });
    });
  });
  print("=============================");

  getCourseInfo("Rose").then((List<String> value) {
    print(value);
  });
  print("=============================");
}

Future<String> getGrade(String courseName) {
  return Future.delayed(Duration(seconds: 3), () {
    return 'Grade: $courseName : 98%';
  });
}

showResult() async {
  String result = await longPress();
  print(result);
}

Future<String> longPress() {
  return Future.delayed(Duration(seconds: 3), () {
    return ("RUSULT of Query: [id:1 name: David]");
  });
}

Future<List<String>> getCourseInfo(String studentName) {
  print("Student $studentName Courses:");
  return Future.delayed(Duration(seconds: 4), () {
    return ['Dart', 'Flutter', 'Java'];
  });
}

Future<Map<String, dynamic>> getStudentName(int id) {
  print("Studnet name is: $id");
  return Future<Map<String, dynamic>>.delayed(Duration(seconds: 3), () {
    return {'id': id, 'studentName': 'Rose'};
  });
}

```
